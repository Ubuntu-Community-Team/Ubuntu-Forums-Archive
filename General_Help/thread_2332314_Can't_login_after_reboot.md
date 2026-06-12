---
title: "Can't login after reboot"
date: 2016-07-30
forum: General Help
---

### Post by maja_ldm on 2016-07-30
I installed 16.04 for my parents, I created an account during installation, then from that account I ran:
```
adduser username
usermod -aG sudo username
```
after which the new user was fine, BUT the original user can't login anymore (the password isn't accepted).

I launched a recovery mode and reset the password with:
```
mount -rw -o remount /
passwd username
```
after which I could login, BUT after a reboot the sotuation as reverted back to not accepting the password.

I read about a few possible commands that could solve similar problems, but I'd like to understand what's going on, or at least how to diagnose this problem.

---

### Post by QDR06VV9 on 2016-07-30
The sudoers file works normally via group membership of a user.

As default, you have the following configuration in ubuntu:

```
 # Members of the sudo group may gain root privileges
 %sudo ALL=(ALL) ALL

```
If I understand your description, you have dropped the group membership for the sudo group.

Hopefully you will still have left another account which is member in the sudo group. If this is true, you can use the following command to fix your user:

```
 sudo usermod -a -G sudo  USERNAME

```
If you have given your root user an explicit password (non standard in ubuntu), you can also invoke:

```
 su -c usermod -a -G sudo  USERNAME
```

If both isn't possible, you may do the following:

    boot your computer with a live/rescue cd (see also... [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode))
    mount your root partition (aka /) to e.g. /mnt
   ```
 chroot /mnt usermod -a -G sudo USERNAME
```

---

### Post by maja_ldm on 2016-07-31
Before trying out the commands, I'm listing the results of *getent*:
```
getent group | grep user1
adm:x:4:syslog,user1
cdrom:x:24:user1
sudo:x:27:user1,user2
dip:x:30:user1
plugdev:x:46:user1
lpadmin:x:113:user1
user1:x:1000:
sambashare:x:128:user1
```
```
getent group | grep user2
sudo:x:27:user1,user2
user2:x:1001:
```
user1 can't login, user2 isn't member of groups that he should have access to. How do I proceed with *usermod*?

---

### Post by steeldriver on 2016-07-31
Since user2 is a member of the sudo group, they should be able to add themself to any other groups

```

sudo usermod -aG adm,cdrom,dip,plugdev,lpadmin,sambashare user2

```

I have no idea why the user1 login would fail after reboot

---

### Post by maja_ldm on 2016-07-31
I remember reading something about the new user being in group *'1001'* and the old user being in group *'1000'*, but it was on my phone and now I can't find it anymore.. or maybe it was about ID's, as I said I can't remember where to look for it.

---

### Post by steeldriver on 2016-07-31
That sounds normal - Ubuntu (like Debian) uses the 'user private group' scheme, so each user gets a primary group with the same name as the user, and with a GID that's typically the same as the UID. The numbering starts from 1000 so user1 gets UID=1000 and GID=1000, user2 gets UID=1001 and GID=1001 and so on. You can then add supplementary groups as required with usermod -aG (or gpasswd, or adduser)

---

### Post by maja_ldm on 2016-07-31
I realized the problem was that the first time I followed the procedure in the OP the system had freezed during reboot and the changes had been lost.
I repeated the procedure and user1 can now login, user2 has gained membership in the other groups and everything is better then before.

---

