---
title: "usb external drive, can't write to it."
date: 2012-11-20
forum: General Help
---

### Post by harreid on 2012-11-20
I have my usb external drive mounted in ubuntan 12.4 and I can read from it, problem  is I can't write to it, I get the message "you are not the owner"   and I can't edit permissions. I'm hoping somebody here can help me. Thank you.  :)

---

### Post by Kirk Schnable on 2012-11-20
Find the path of your external drive, it's probably in /media, so run

```
ls /media
```If anything in there looks familiar, that's your drive.  If there's only one folder, and it looks like random letters and numbers, it's probably your drive if that's the only USB storage plugged in.

Verify that it's your drive by viewing its contents.  If your drive is called YourDrive:

```
ls /media/YourDrive
```

That being said, you can easily give your user permission to modify the files on the drive.  If your username is UbuntuUser and your hard drive is YourDrive, run:

```
chown -R UbuntuUser /media/YourDrive
```This should clear up the permissions issues.

Kirk

---

### Post by harreid on 2012-11-21
> **Kirk Schnable said:**
> Find the path of your external drive, it's probably in /media, so run

```
ls /media
```If anything in there looks familiar, that's your drive.  If there's only one folder, and it looks like random letters and numbers, it's probably your drive if that's the only USB storage plugged in.

Verify that it's your drive by viewing its contents.  If your drive is called YourDrive:

```
ls /media/YourDrive
```

That being said, you can easily give your user permission to modify the files on the drive.  If your username is UbuntuUser and your hard drive is YourDrive, run:

```
chown -R UbuntuUser /media/YourDrive
```This should clear up the permissions issues.

Kirk
Thanks for helping Kirk,

I did as you suggested and got the following, I don't know what to do from here, can you help me again please.

Thank you.

harry@ubuntu:~$ ls /media/harry
backup  lost+found  usr
harry@ubuntu:~$ chown -R harry /media/harry
chown: changing ownership of `/media/harry/usr/lib/opkg/info': Operation not permitted
chown: changing ownership of `/media/harry/usr/lib/opkg': Operation not permitted
chown: changing ownership of `/media/harry/usr/lib': Operation not permitted
chown: changing ownership of `/media/harry/usr': Operation not permitted
chown: cannot read directory `/media/harry/lost+found': Permission denied
chown: changing ownership of `/media/harry/backup/enigma2settingsbackup.tar.gz': Operation not permitted
chown: changing ownership of `/media/harry/backup': Operation not permitted
chown: changing ownership of `/media/harry': Operation not permitted
harry@ubuntu:~$

---

### Post by kclark on 2012-11-21
Looks like you need to use sudo

```

sudo  chown -R harry /media/harry

```

---

