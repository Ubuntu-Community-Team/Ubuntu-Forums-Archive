---
title: "[SOLVED] Frustrated!!!"
date: 2007-09-25
forum: General Help
---

### Post by tech9 on 2007-09-25
ok, this is the second time that I tried restoring my system and upon bootup it just freezes on me.

2nd time same error message:

Error Message:

/bin/sh: can't access tty; job control turned off
(initramfs)

I ran this command to backup my files...

tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I thought by excluding /etc/fstab, that the UUIDs would be fine when creating a new partition...

Somewhere in the system there are more files that are related to this and need to be excluded.

I ran tar xvpfz backup.tgz -C / to restore...

Can anyone help me figure out what I need to do to fix this?... Is it possible to work from the liveCD. I believe there are a lot of file that are locked when using liveCD


Maybe this backup command is not the solution, but I wanted to be able to restore all my settings, programs, system changes, background ect.

I am not ready to give up on Ubuntu just yet, but backup and restore processes are proving to be a pain](*,)

Is there any better solution to backup besides tar, sbackup, part image, and clonezilla?

---

### Post by lavajumper on 2007-09-25
Backups are never as simple as they should be ;)
Have you tried searching "backup" in synaptic? There may be something there that does what you're trying to do.

Also, I never backup /dev, it gets build dynamically on boot.

---

### Post by danbh on 2007-09-25
maybe you just need to backup your /home directory...

I thought that had all of your settings and whatnot.

---

### Post by tech9 on 2007-09-27
> **danbh said:**
> maybe you just need to backup your /home directory...

I thought that had all of your settings and whatnot.


Backing up just my home directory will not not capture/backup my applications [-(

---

### Post by tech9 on 2007-09-27
> **lavajumper said:**
> Backups are never as simple as they should be ;)
Have you tried searching "backup" in synaptic? There may be something there that does what you're trying to do.

Also, I never backup /dev, it gets build dynamically on boot.

I have tried that as well and have not found anything. :roll:

---

### Post by tech9 on 2007-09-27
I have solved this issue....

[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

---

