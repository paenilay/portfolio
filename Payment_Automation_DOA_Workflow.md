# Payment Automation DOA (Delegation of Authority) Workflow

## Workflow Overview

### Step 1 – Request Submission
The requester submits a payment request through Microsoft Forms.

Power Automate automatically:
- Captures form data
- Creates a record in Microsoft Lists
- Generates a tracking ID
- Starts the approval workflow

### Step 2 – Approval Routing
Power Automate checks the requested amount and determines the approver:

#### Amount 1
Approval request is sent to the Level 1 Head via:
- Microsoft Teams Approval Card
- Email Notification

#### Amount 2
Approval request is sent to the Level 2 Head.

#### Amount 3
Approval request is sent to the Level 3 Head.

Approval status is updated automatically in Microsoft Lists.

### Step 3 – FM Approval
After Level 1, Level 2, or Level 3 Head approval:
- Request is routed to FM
- FM receives approval notification through Teams and Email
- Decision is recorded in Microsoft Lists

If FM rejects:
- Workflow ends
- Requester receives rejection notification

### Step 4 – Cash Collection
If FM approves:
- Cash Collection team receives notification
- Payment processing begins
- Status is updated to Completed

### Step 5 – Closure
Power Automate:
- Updates Microsoft Lists
- Sends completion notification
- Archives approval history for audit purposes

## Business Benefits
- Eliminates paper-based approvals
- Faster approval turnaround time
- Full audit trail in Microsoft Lists
- Automatic email and Teams notifications
- Reduced manual follow-up
- Centralized approval tracking and reporting

## Workflow Logic

```text
Request Form
    |
    v
Check Amount
    |
    +--> Amount 1 --> Level 1 Approval
    |
    +--> Amount 2 --> Level 2 Approval
    |
    +--> Amount 3 --> Level 3 Approval
                    |
                    v
              FM Approval
                    |
            +-------+-------+
            |               |
          Reject         Approve
            |               |
        Workflow End   Cash Collection
                            |
                            v
                           End
```
