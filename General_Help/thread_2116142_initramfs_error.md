---
title: "initramfs error"
date: 2013-02-15
forum: General Help
---

### Post by sharmaneha on 2013-02-15
I have Ubuntu 10.04 dual boot with Windows 7 on my computer. I have been experiencing a recurring problem for the past couple of days:
When I boot Ubuntu it gives the "initramfs" error and lot of other code that I don't understand.

And this is what I have been doing to solve it (based on reading solutions on blogs,how-tos etc):

1.I boot Windows
2.Run cmd promt & run the following command
    [FONT="Fixedsys"]chkdsk c: /f[/FONT]
  which returns the following:
   [FONT="Fixedsys"]The type of the file system is NTFS. Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another process. Would you like to schedule this volume to be checked the next time the system restrart (Y/N) y

This volume will be checked the next time system restarts[/FONT]

So I restart Windows again to allow it go through with the disk check process
3.After that I boot Ubuntu using a Live CD.
4.And enter the following in terminal 
  [FONT="Fixedsys"]sudo fdisk -l[/FONT]

then

  [FONT="Fixedsys"]sudo fsck /dev/sda6[/FONT]
5.I shut down my computer, remove live cd and start ubuntu again and it works... only for a couple of days.

Please advice on what I am doing wrong. Any help will be appreciated. Thanks.

---

### Post by dino99 on 2013-02-15
you might have some hdd cluster issues, as you get inode errors. What says hdparm ?

---

### Post by sharmaneha on 2013-02-15
> **dino99 said:**
> you might have some hdd cluster issues, as you get inode errors. What says hdparm ?
a lot of things..

    neha@FreeWorld:~$ hdparm

    hdparm - get/set hard disk parameters - version v9.15

    Usage:  hdparm  [options] [device] ..

followed by a list of options. I am not sure what to do with it

---

