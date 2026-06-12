---
title: "Looking for a program to copy the system"
date: 2019-09-14
forum: General Help
---

### Post by frollog on 2019-09-14
Greetings!
I am looking for a solution to a problem. We have a dedicated server with RAID 1 and Ubuntu 16.04. We want to copy the installed system with all the packages and settings to a virtual VDS-KVM server without a RAID. Copying must be done through the generation of an ISO image of the system and its further installation. At the same time, some folders that take up a lot of space should be excluded from copying.
Please tell me, is there a program with which I can solve the problem?
Maybe there is a commercial version to implement this?
PS I tried using remastersys, but an error was immediately generated when the image was launched.
Regards, Ivan

---

### Post by Skaperen on 2019-09-14
are you doing a CDROM or DVD image?

i recommend purchasing a large 2TB, 3TB, or 4TB external USB hard drive if your server can do high-speed USB 2.0 or better yet 3.0 (blue tab).  this will solve lots of problems.  if you are considering commercial software you must be open to spending money for this.  i have 3 of the 2TB ones.  they make it nice to move data around and take a backup to offsite (home).

---

### Post by HermanAB on 2019-09-14
Hmm, some suggestions:
Copying over ethernet may be much easier and faster than over removable media.
It is usually better to save the list of packages and then reinstall from scratch on the new hardware.
You can copy the settings from /etc later once the new machine is running.

The Debian auto install system is called Preseed:
[https://wiki.debian.org/AutomatedInstallation](https://wiki.debian.org/AutomatedInstallation)
[https://wiki.debian.org/DebianInstaller/Preseed](https://wiki.debian.org/DebianInstaller/Preseed)

---

### Post by Artim on 2019-09-14
One of my favorites is [SystemBack]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10").  It allows you to make a bootable .iso of your installed system, and you can include your /home directory if you like.

---

### Post by frollog on 2019-09-20
Many thanks for the answers.

---

### Post by lensman3 on 2019-09-25
There is always the old standby:

[INDENT]1) mkdir <TARGET DIR>

[INDENT][/INDENT]2) cd <FROM DIR>

[INDENT][/INDENT]3) tar cf - . | ( cd <TARGET DIR> ; tar xBf - )[/INDENT]

Tar has several ways to limit the size of files to copy and removing large directories.  

Making a bootable ISO will require running grub in one form or another because the address of the entry point of the kernel will need to be need added to the boot code.

---

