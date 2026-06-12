---
title: "Please clarify the differences between root user and administrator account"
date: 2012-10-23
forum: General Help
---

### Post by dr1094 on 2012-10-23
What is the difference between the root account i.e. the account created through installation, and the desktop account which I created later and upgraded to be Administrator.

[System > Administration > Users and Groups > advanced settings > user privileges] shows that the administrator account has more privileges than the root account (which shows up as a Custom type account), why is this? Does that mean administrator account (acct2) has more power over the system than the root account (acct1).

What I am worried about is that I might cause serious harm to the system through the administrator account(acct2). plus, from the reading I have done so far, I think I am misunderstanding the concept of root, and its ability/capability. 

Do I as an administrator(acct2) have the capability of jeopardizing the entire system? or is that something only the root user can do?

---

### Post by lykwydchykyn on 2012-10-23
On a Linux system, nobody has more privileges than root (UID 0).  Root has implicit access to everything, so even if there are not explicit permissions to something for root, it has permissions.  The operating system basically runs as root.

An administrator account in Ubuntu is basically an account that has access to sudo, and membership in some groups that give it access to some additional files (logs, for example).

The account you create when you install Ubuntu is *not* root (though root is created implicitly during the install, in a sense).  It's just a regular user account with administrative privileges.

---

### Post by Cheesemill on 2012-10-23
The account created when you install ***isn't*** a root account. It's an account with admin privileges just like the one you have created after installation.

---

