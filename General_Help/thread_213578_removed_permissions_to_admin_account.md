---
title: "removed permissions to admin account"
date: 2006-07-11
forum: General Help
---

### Post by christinel4t on 2006-07-11
My friend did not want his son to mess up the computer so he decided to change the main account to a non-admin account and then set up a new admin account that his son couldn't access.  _Unfortunatly_, he decided to change the permissions on the main account before he created the new account.  Now he has no account with admin or sudo permissions, and when I try to boot to recovery mode and it asks for root password I get a login error and if I hit cntrl+d to continue, I then can't write changes to /etc/group or /etc/sudoers because I am not the owner and even chmod doesn't work.

---

### Post by Paerez on 2006-07-11
ok so first put your ubuntu cd in the drive an boot your computer live (dont worry, this won't mess up your install).

Once it is booted, find out what the name of the root partition is. Do this by opening a terminal and typing:
```
# mount
```
There should be something like:
```
/dev/hda1 on /media/hda1 type ext3
```
this is your root partition. Then type:
```
# sudo chroot /media/hda1
# passwd root
```
and enter the new root password.

Hope that works.

---

### Post by christinel4t on 2006-07-11
May the road rise up to meet you.  An old Irish blessing I heap upon you.

It works thanks

---

### Post by Paerez on 2006-07-11
"may the road rise up to meet you"

that always happens to me when I spin around too much. I think I am falling on my face but it really feels like the floor comes to me...

glad you got it.

---

