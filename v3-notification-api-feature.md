# Notification API Feature Proposal
Updated by: Aeriel

## Goal
- Enhances the existing push notification functionality by adding the capability to save notifications in our database
- Replace the old v2 notifications implementation that is only used for intake form

## Notification Schema
| Name | Data Type | Description |
|-|-|-|
| referenceId | UUID | Unique identifier for each notification |
| username |STRING | Assigned username |
| title | STRING | Notification title |
| message | STRING | Notification description |
| data | OBJECT | Other metadata that is used in the mobile app |
| viewedAt | DATE or NULL | (Optional) Determines if the user has viewed the notification or not |
| createdAt | DATE | Date and time of record creation |
| updatedAt | DATE | Date and time of last record update |

## API Endpoints

### Get Notifications
```
GET /api/v3/notifications
```
**Sample Response**
```
{
  referenceId: xxxxxxxxxxxx,
  type: "payment",
  title: "Pouch · Payment Complete",
  message: "You have received P100.00 from juandelacruz`,
  viewedAt: null, // Date
  createdAt: 2022-06-30T10:11:08.848+00:00,
  createdAt: 2023-10-09T07:21:27.525+00:00
}
```

### Get Notifications Count
```
GET /api/v3/notifications/count
```
This will be used in the wallet screen to show if there are unread notifications. This will be mainly used for submitting on-chain deposit form.

**Sample Response**
```
{
  total: 21,
  unread: 2
}
```

## Diagrams
![image](https://github.com/pouch-ph/docs/assets/31103697/7560ab9a-1c05-42ce-9790-0035d132b6d0)

![image](https://github.com/pouch-ph/docs/assets/31103697/80d2fd0c-1a39-40e2-89de-6fba0f3d7455)

![image](https://github.com/pouch-ph/docs/assets/31103697/16d390a1-f1b0-4634-85e6-b77b03b99fa2)

## Sample Mockup
|Wallet Screen|Notifications Screen|
|-|-|
|![image](https://github.com/pouch-ph/docs/assets/31103697/6509e4a5-9e72-44e3-b1ee-6ad20255b0d7)|![image](https://github.com/pouch-ph/docs/assets/31103697/2ab3ba17-b528-4827-b4bd-af3e2965d409)|

