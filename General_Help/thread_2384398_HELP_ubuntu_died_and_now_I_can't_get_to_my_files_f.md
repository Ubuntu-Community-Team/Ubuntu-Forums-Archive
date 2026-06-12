---
title: "HELP: ubuntu died and now I can't get to my files from Ubuntu live"
date: 2018-02-06
forum: General Help
---

### Post by omai-bokhari on 2018-02-06
Hello all,
Unfortunately I got a "blue screen of death" on ubuntu 16.04 LTS. at first I was working on my project just fine, and then when I tried to view an image it wouldn't open my image files. So I thought maybe because I haven't updated my software something is acting up. So then when I tried to open update manager, nothing was happening, it wasn't showing all the text in boxes.
So i thought if I restart my laptop it would help. When I tried to restart I got a blue screen after ubuntu seemed to be booting up. Tried over and over but nothing. Using lenovo thinkpad T530 and ran checks on the hardware and seems to be working fine..

So I put in an ubuntu bootable usb, so I could at least get to my files. Now, I am using ubuntu live to type this, but cannot access my harddrive. 
This is the message I get when I try to mount my hardddrive

Error mounting /dev/sdb1 at /media/ubuntu/Ubuntu 16.04.3 LTS amd64: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdb1" "/media/ubuntu/Ubuntu 16.04.3 LTS amd64"' exited with non-zero exit status 32: mount: /dev/sdb1 is already mounted or /media/ubuntu/Ubuntu 16.04.3 LTS amd64 busy

please help... Keep in mind I am basically a Noob and although with step-by-step instructions I can make do, I have no computing/coding experience by any stretch and only use my computer when necessary.. I just happen to use ubuntu because I like open source everything.

Thank YOU

EDIT: ook I was able to get into my files using sudo nautilus... but WHAT WTH happened to ubuntu :(

---

### Post by Impavidus on 2018-02-07
> **omai-bokhari said:**
> 
Error mounting /dev/sdb1 at /media/ubuntu/Ubuntu 16.04.3 LTS amd64: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdb1" "/media/ubuntu/Ubuntu 16.04.3 LTS amd64"' exited with non-zero exit status 32: mount: /dev/sdb1 is already mounted or /media/ubuntu/Ubuntu 16.04.3 LTS amd64 busy

That looks like an attempt to mount your live disk, not your Ubuntu partition on your hard drive.

What could have happened? Difficult to say. A broken hard drive, loose cable, computer overheating, a random bitflip caused by a decaying carbon-14 atom or something else. Make some more backups of your files and run a file system check.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by omai-bokhari on 2018-02-07
> **Impavidus said:**
> That looks like an attempt to mount your live disk, not your Ubuntu partition on your hard drive.

What could have happened? Difficult to say. A broken hard drive, loose cable, computer overheating, a random bitflip caused by a decaying carbon-14 atom or something else. Make some more backups of your files and run a file system check.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

well I was running on the live disk and trying to get into the harddrive, but thankfully I did get through.

Is it better to do the file system check or just wipe it after i back up and start all over? THANK YOU!

---

### Post by Impavidus on 2018-02-07
If a file system check fixes it, reinstalling is overkill. If your hardware is broken, reinstalling won't fix it.
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by omai-bokhari on 2018-02-07
This app says "disk is OK" 
so i'm all set then to reinstall?

---

