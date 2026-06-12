---
title: "Messed Up Administration (dapper)"
date: 2006-11-26
forum: General Help
---

### Post by casper911ca on 2006-11-26
Hello,

New forum member here.

I'll cut to the chase. When I was palying around with the users and groups (System>Admistration>Users and Groups) I checked a box to disable admistration tasks for the main user... the only user...oops. And now I'm left with no way to fix it. I tried sudo passwd root, so to enable a root password but i still cant login with admistrators rights ( i guess before hand i failed to enable super user GDM logins when in the users and groups dialog). So to enable my the root privelges again I have to be root, which is imppossible because i disabled it, catch 22. Is there some cleaver way to re-enable root privelger or to login to a root account so i can fix this?

I googled for 2 hours trying to find an answer with no success.

Ubuntu 6.06 LTS Dapper Drake.

-casper911ca

---

### Post by aysiu on 2006-11-26
Have you tried this?
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by CatKiller on 2006-11-26
When you restart the computer, press Escape to enter the GRUB menu.

Select the recovery mode. This will automatically log you in as root.

I believe the commands you'll need are

```
adduser casper911ca admin
adduser casper911ca adm
``` substituting **casper911ca** with whatever your user name is.

Reboot and cross your fingers :)

Basically, you're adding yourself to the **admin** and **adm** groups, in case I've got the syntax wrong somewhere.

EDIT: You can write a post so much quicker if you've already got it written out in some handy useful user guide :)

---

### Post by casper911ca on 2006-11-26
That did it! Thank you!

---

