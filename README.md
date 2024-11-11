# digital_party

## AWS Architecture

![infra_architecture](https://github.com/user-attachments/assets/9b442a7e-4a58-4bce-98f1-a01dfe24ce13)

# Digital Governance Application Documentation

## 1. Entities and Data Structures

### Party

| Attribute   | Type   | Description                                         |
|-------------|--------|-----------------------------------------------------|
| party_id    | String | Unique identifier for the party                     |
| name        | String | Name of the party                                   |
| regions     | List   | List of regions associated with the party           |
| teams       | List   | List of teams associated with the party             |
| members     | List   | List of members belonging to the party              |
| youth_org   | Object | Youth Organization associated with the party        |

### Region

| Attribute   | Type   | Description                                         |
|-------------|--------|-----------------------------------------------------|
| region_id   | String | Unique identifier for the region                    |
| name        | String | Name of the region                                  |
| admin       | Object | Admin assigned to the region                        |
| mp          | Object | MP associated with the region                       |
| teams       | List   | List of teams within the region                     |

### Team

| Attribute   | Type   | Description                                         |
|-------------|--------|-----------------------------------------------------|
| team_id     | String | Unique identifier for the team                      |
| name        | String | Name of the team                                    |
| region      | Object | The region the team is part of                      |
| admin       | Object | Team admin                                          |
| members     | List   | List of members in the team                         |

### Member

| Attribute     | Type    | Description                                        |
|---------------|---------|----------------------------------------------------|
| member_id     | String  | Unique identifier for the member                   |
| name          | String  | Name of the member                                 |
| role          | Enum    | Role assigned to the member (e.g., Team Admin)     |
| team          | Object  | Team association                                   |
| region        | Object  | Region association                                 |
| youth_member  | Boolean | Indicates if the member is in the Youth Org        |
| volunteer     | Boolean | Indicates if the member is a volunteer             |

### Youth Organization

| Attribute     | Type    | Description                                        |
|---------------|---------|----------------------------------------------------|
| youth_org_id  | String  | Unique identifier for the Youth Organization       |
| admin         | Object  | Admin of the Youth Organization                    |
| members       | List    | List of members within the Youth Organization      |

---

## 2. Roles and Permissions

### Roles Overview
1. **Member** – General user of the platform.
2. **Team Admin** – Manages a regional team.
3. **MP** – Represents a region in Parliament.
4. **President** – Leader of the party.
5. **Party Admin** – Administrator of the digital platform.
6. **Youth Org Admin** – Manages the Youth Organization.
7. **Volunteer** – Supports specific tasks or campaigns.

### Permissions Matrix

| Role           | Party              | Region              | Team              | Member            | Youth Org         |
|----------------|--------------------|---------------------|-------------------|-------------------|-------------------|
| Party Admin    | Full Access        | Manage             | Manage           | Manage           | Manage           |
| Team Admin     | View               | View               | Manage           | View Team Members | None             |
| MP             | View               | Post Updates       | View             | View Region Members | View Youth Org Members |
| President      | Full Access        | Manage             | Full Access      | Full Access      | View             |
| Youth Org Admin| None               | None               | None             | Manage Youth Members | Full Access   |
| Volunteer      | None               | None               | View, Join       | View Profile     | Participate       |
| Member         | View               | View               | Join             | View Profile     | Participate if eligible|

---

## 3. Functional Specifications

- **Member:** Participates in discussions, accesses general content, and joins teams.
- **Team Admin:** Manages team members, events, and communications within a team.
- **MP:** Posts updates relevant to their constituency and collaborates with team admins.
- **President:** Leads the party, provides guidance, and posts global announcements.
- **Party Admin:** Oversees the platform, manages user roles, and ensures system integrity.
- **Youth Org Admin:** Manages youth members, events, and youth-specific initiatives.
- **Volunteer:** Participates in campaigns, assists with events, and supports the party’s efforts.

---

This consolidated structure minimizes redundancy by integrating attributes, roles, and permissions, while maintaining clarity across sections. Let me know if you'd like any further adjustments!
