---
title: "[SOLVED] Unable to add a printer on Gutsy"
date: 2007-12-11
forum: General Help
---

### Post by aspa on 2007-12-11
I'm unable to add a new printer on Gutsy.
I've started the New Printer wizard through System / Administration / Printing.
After clicking through the dialogs I finally get the following prompt:

Password required
Password for foo on localhost?

My local password is not accepted in this dialog and the system keeps giving me the password prompt.

Which password is the system asking for?

I'm not sure if this is related or not but for some reason the System / Administration menu only includes 6 items and e.g. the Synaptic package manager is missing.

---

### Post by jdaiker on 2007-12-12
Just went through this issue myself... my suggestion is as follows:

Make sure that you are a member of the lpadmin group.  I compared my /etc/group file between my old feisty install and my new gutsy install, and noticed this different.

System -> Administration -> Users and Groups
"Manage Groups"
lpadmin -> "Properties"
Check your username in the box that appears.

I didn't have to logout/login... but YMMV.

Hope that helps.

John Daiker

---

### Post by aspa on 2007-12-14
For some reason most of the system / admin menu items such as "users and groups" don't appear in the list anymore but manually adding my account to the lpadmin group fixed the problem.

thanks!

---

