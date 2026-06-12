---
title: "[SOLVED] Removing sudo for users"
date: 2008-01-17
forum: General Help
---

### Post by mgw854 on 2008-01-17
I have a kid that thinks that he is and uber geek- he "upgrades" Ubuntu continually on a machine that he has access to, and "fixes" problems.  In reality, all he does is mess things up.  I know a bit more about Linux than him, but not much more.  I've done a fresh install of 7.10, but before he messes anything more up, I need to find out how to remove his sudo permissions.  I've read some stuff about visudo and sudoers, but I can't figure out how to REMOVE all permissions.  I'm comfortable using these tools, I just don't have the syntax down.  Could anyone please give me the line to add to prevent his account (student) from having sudo permissions, but while allowing my account (mgw854) to still have them?

---

### Post by Sef on 2008-01-17
Go into his account and there is a box that you can set his permissions from.

System > Administration > Users and Groups > highlight his user name > click on Properties > User Privileges > uncheck 'Administer the System'.

---

