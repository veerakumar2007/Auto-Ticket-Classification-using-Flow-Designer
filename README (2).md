# Auto Ticket Classification Using Flow Designer

## Project Overview

This project is a ServiceNow-based IT helpdesk automation system.

The system automatically classifies IT support tickets based on the issue description. It uses Flow Designer to identify the issue and automatically set the Category and Subcategory.

The project is designed for a school IT helpdesk where common issues include Wi-Fi problems, projector problems, password/login issues, and slow computers.

## Objectives

- Automatically classify IT support tickets.
- Reduce manual ticket classification.
- Automatically assign Category and Subcategory.
- Improve ticket routing and management.
- Send an email confirmation to the caller.
- Provide a simple and maintainable no-code solution.

## Technology Used

- ServiceNow
- Flow Designer
- Update Sets
- Custom Tables
- Choice Fields
- Reference Fields
- Email Notifications

## Business Requirements

The system should:

1. Automatically classify a ticket when it is created.
2. Identify the issue from the Short Description.
3. Set the appropriate Category.
4. Set the appropriate Subcategory.
5. Maintain dependent Category and Subcategory values.
6. Send an email confirmation to the caller.
7. Store ticket information in a structured table.
8. Support future improvements and extensions.

## Project Architecture

```text
User
  |
  v
Create IT Support Ticket
  |
  v
Incident WorkFlow Table
  |
  v
Flow Designer
  |
  +--> Wi-Fi ---------> Network
  |
  +--> Projector ------> Hardware
  |
  +--> Password/Login -> Access
  |
  +--> Slow/Hanging --> Performance
  |
  v
Send Email Confirmation
  |
  v
Ticket Updated
```

## Custom Table

Table Name: `Incident WorkFlow`

The custom table contains the following fields:

| Field | Type |
|---|---|
| Number | Auto Number |
| Caller | Reference - sys_user |
| Category | Choice |
| Subcategory | Choice |
| Short Description | String |
| Description | String |
| State | Choice |
| Assigned Group | Reference - sys_user_group |
| Assigned to | Reference - sys_user |

## Category and Subcategory

| Issue | Category | Subcategory |
|---|---|---|
| Wi-Fi | Network | Wi-Fi |
| Projector | Hardware | Projector |
| Forgot Password | Access | Forgot Password |
| Slow Computer | Performance | Slow Computer |

## Flow Designer

Flow Name:

`Auto Classify School IT Tickets`

### Trigger

- Trigger: Record Created
- Table: Incident WorkFlow
- Condition: Category is Empty

### Classification Rules

The flow checks the ticket description and classifies the ticket.

```text
WiFi / Network
     |
     v
Category = Network
Subcategory = Wi-Fi


Projector
     |
     v
Category = Hardware
Subcategory = Projector


Password / Login
     |
     v
Category = Access
Subcategory = Forgot Password


Slow / Hanging
     |
     v
Category = Performance
Subcategory = Slow Computer
```

## Email Notification

After classification, the flow sends an email to the caller.

Subject:

`Your Request for the issue has been submitted.`

The email provides confirmation that the request has been submitted.

## Testing

### Test 1: Wi-Fi Issue

Input:

`WiFi not working in library`

Expected result:

- Category: Network
- Subcategory: Wi-Fi
- Email confirmation sent to caller

### Test 2: Projector Issue

Input:

`Projector not turning on`

Expected result:

- Category: Hardware
- Subcategory: Projector
- Email confirmation sent to caller

## Deployment

The project uses a ServiceNow Update Set named:

`Project Update Set`

Before deployment:

1. Complete the configuration.
2. Make the Update Set complete.
3. Export the Update Set as XML.
4. Import it into the required ServiceNow instance.

## Key Features

- Automatic ticket classification
- Category and Subcategory assignment
- Dependent choice fields
- Email confirmation
- No-code Flow Designer automation
- Structured ticket management
- Easy maintenance and future expansion

## Future Enhancements

Possible future improvements include:

- Automatic assignment to support groups
- SLA tracking
- More ticket categories
- Advanced classification
- Predictive intelligence
- Additional automation

## Conclusion

The Auto Ticket Classification Using Flow Designer project provides an automated way to classify school IT support tickets.

By using ServiceNow Flow Designer, the project reduces manual classification work and improves the organization of support requests. The solution is simple, maintainable, and can be extended with additional automation features in the future.

## Project Information

Project: Auto Ticket Classification Using Flow Designer

Platform: ServiceNow

Main Tool: Flow Designer
