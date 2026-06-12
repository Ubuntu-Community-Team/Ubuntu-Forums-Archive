---
title: "Lost password"
date: 2008-03-16
forum: General Help
---

### Post by Winston Forde on 2008-03-16
I have  a Notebook AJP LAptop but cannot remember my password.   Is there any way I can get into my laptop?

---

### Post by kellemes on 2008-03-16
The password of the bios?
Or the password of your Ubuntu installation?

---

### Post by nick_h on 2008-03-16
To recover an Ubuntu password look [here](https://help.ubuntu.com/community/LostPassword).

---

### Post by Xtreme it on 2008-03-17
Probably you have solved this issue already, but I'll post here how I solved a similar issue.

I had a machine with an unknown user/password and root was disabled for login (anyway I didn't knew the password so...).

My quick solution:
[LIST=1]
[*]Started a liveCD distribution (Ubuntu 7.10).
[*]Mounted the disk that was in the computer.
[*]Made a backup copy of the file /etc/shadow
```
sudo cp /etc/shadow /etc/shadow.bk
```
[*]Opened the /etc/shadow file (used it for identifying the user name, and change the password).
```
sudo vi /etc/shadow
```
[*]In other shell, created a new MD5 hash for the new password (run the command, it will ask twice for the password and show the hash).
```
grub-md5-crypt
```
[*]Copy/Paste the hash, in place of the previous password (in /etc/shadow file) - the hash should start with '$1$'.
[*]Reboot and use the new user/password pair.
[/LIST]

Hope this will help someone.

---

### Post by bodhi.zazen on 2008-03-17
Wow, that is the hard way :)

Easiers way is to boot to recovery mode and enter :

```
passwd <user>
```

Where password is the user needing the password reset.

If you can not do that (because you set a root password and can not boot to recovery mode), boot the Live CD and use chroot.

```
sudo mount /dev/sdxy /mnt

sudo chroot /mnt /bin/bash

passwd root

passwd <user>
```

Where /dev/sdxy is your Ubuntu root partition.

Reboot to hard drive.

---

