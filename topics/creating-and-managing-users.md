[//]: # (title: Creating and Managing Users)
[//]: # (auxiliary-id: Creating and Managing Users;Managing Users and User Groups)

## What is User Account in TeamCity
{id="User+Account" auxiliary-id="User Account"}

_User account_ is a combination of username and password that allows TeamCity users to sign in to the server and use its features. User accounts can be created manually, or automatically upon sign in depending on used authentication scheme (refer to the [Authentication Modules](authentication-modules.md) section for more details).

Each user account:
* Has an associated role that ensures access to all or specific TeamCity features through corresponding permissions. Learn more about [roles and permissions](managing-roles-and-permissions.md).
* Belongs to at least one user group. Learn more about [user groups](creating-and-managing-user-groups.md).

In addition to authenticated users, there is a special user account for non-registered users called [Guest User](guest-user.md). It allows browsing TeamCity projects without authorization. By default, guest login is disabled.

Only users with the respective permissions can create and edit other user accounts on the TeamCity server.

## Creating New User

The __Administration | Users__ page provides the _Create user account_ option.

When creating a user account when [several authentication modes enabled](configuring-authentication-settings.md#Enabling+Multiple+Authentication+Modules) on the server, only a username is required.

If only the [default authentication](authentication-modules.md) is used, the password is required as well. Any new user is automatically added to the [All Users group](creating-and-managing-user-groups.md#%22All+Users%22+Group) and inherits the roles and permissions defined for this group. If you do not use [per-project permissions](managing-roles-and-permissions.md#Authorization+Mode), you can specify here whether a user should have administrative permissions or not. Otherwise, you can assign roles to this user [later](#Assigning+Roles+to+Users).

<anchor name="ManagingUsersandUserGroups-EditingUserAccount"/>

## Editing User Account

To edit an existing user account, go to the __Administration | Users__ page and click the name of the user. The page provides several tabs allowing you to modify various user account settings

### General

The __General__ tab allows modifying the username, email address, and password. Users can change their own username only if free registration is allowed on the server. The administrator can always change the username of any user.

#### Authentication Settings

The __Authentication Settings__ section appears if several authentication modules are enabled on the server. Here you can edit usernames for different authentication modules such as LDAP and Windows Domain.

You can map external OAuth usernames with an existing TeamCity user. If a user with the respective username signs in to TeamCity via OAuth, TeamCity will be able to recognize them.

<anchor name="vcsUsername"/>
<anchor name="ManagingUsersandUserGroups-vcsUsername"/>

### VCS Usernames

This tab allows viewing and editing default usernames for different VCSs used by the current user.   
Multiple usernames are supported for a VCS root type and for a separate VCS root: several newline-separated values can be used for each VCS username.

The names set here will be used to:
* show builds with changes committed by a user with such a VCS username on the [Changes](viewing-your-changes.md) page
* highlight such builds on the Projects page if the appropriate [option is selected](configuring-your-user-profile.md#Customizing+UI),
* notify the user on such builds when the __Builds affected by my changes__ option is selected in [notifications settings](adding-notification-rules.md#What+Will+Be+Watched).

## Add User to Group

Use the __Groups__ tab to view the [groups](creating-and-managing-user-groups.md) the user belongs to and add/remove the user from groups.

## Add User to Project

To add a user to a specific project and manage permissions this user has in it, you need to assign them with a certain role. Read how to [manage roles](managing-roles-and-permissions.md#Managing+Roles).

The __Roles__ tab for a user is available only if per-project permissions are enabled on the server __Administration | Authentication__ page_. You can view this tab to view the roles assigned to the user directly and those inherited from groups. The roles assigned directly can be modified/removed here.

<anchor name="assigningRoles"/>
<anchor name="ManagingUsersandUserGroups-Assigningrolestousers"/>

## Assigning Roles to Users
[//]: # (AltHead: assigningRoles)

To be able to grant roles to users on per-project basis, enable per-project permissions on the __Administration | Authentication__ page. The __Administration | Roles__ page lists all existing roles detailing their permissions.

There are several ways to assign roles to one or several users:
* To assign a role to a specific user, on the __Users__ tab for the user click _View roles_ in the corresponding column. In the __Roles__ tab, click __Assign role__.
* To assign a role to multiple users, on the __Users__ tab, check the boxes next to the usernames and use the __Assign roles__ button at the bottom of the page.
* To assign a role to all users in a group, on the __Groups__ tab click _View roles_ for the group in question, then assign a role on the group level.

When assigning a role, you can:
* Select whether a role should be granted globally, or in particular projects.
* Replace existing roles with the newly selected. This will remove all roles assigned to user(s)/group and replace them with the selected one instead.

## Notification Rules

This tab displays [notification rules](adding-notification-rules.md) for the user:
* __Own rules__: rules configured by the user are displayed here and can be modified.
* __Inherited rules__: rules inherited by the user from the groups they belong to.

## Adding Multiple Users to Group

On the __Administration | Users__ page, select users, click the __Add to groups__ button at the bottom, and specify the groups to add the users to. Note that all these users will inherit the roles defined for the group.