---
title: "System crash inodes"
date: 2008-06-18
forum: General Help
---

### Post by artisan on 2008-06-18
I've been looking through the forums. Am I one of the only ones that has a system hang?
I end up having to reboot and clean up something called inodes. (a long list)
Lets say that firefox crashes and I attempt to restart firefox I get a the usual icon on the bottom task bar, except the icon just says close firefox. Then I know I have a system hang. Once this has happened I cannot get into system monitor to close firefox manually.
Another example Applications>Sound & video>Rythmbox. If it fails to open first time (pretty usual) and I click on the link again, I get a System lock and I am unable to get into system monitor to close it down.
I am running HH and have just installed the last big update and was hoping that the update would clean up this issue.
Does anyone have a suggestion where I can look for a solution. A quick look through the forums for "inodes" and a solution but, I seem to be alone with this issue:(
Thanks

---

### Post by iaculallad on 2008-06-18
Try executing badblocks command to your Filesystem drive if it reports any errors.

```
badblocks /dev/filesystem_drive
```

---

### Post by sdennie on 2008-06-18
This sounds like it could be a hardware problem.  Is your disk very old?

---

### Post by artisan on 2008-06-18
Thanks. I need a little more info. It is a long time since I used the command prompt:(
> **iaculallad said:**
> Try executing badblocks command to your Filesystem drive if it reports any errors.

```
badblocks /dev/filesystem_drive
```

And it is a brand new system, i.e. new hard drives.
I bought the computer a month or so ago and the install by the shop was screwed. 
I am running two hard drives. The first has windows, used and not registered (so ?? I don't use) and a second drive. I use HH on the second drive. 
This is where the problem starts. I manually choose Ubuntu from a boot menu by pressing F11 when the system is booting up.

---

### Post by iaculallad on 2008-06-18
> **artisan said:**
> Thanks. I need a little more info. It is a long time since I used the command prompt:( .

Navigate to Applications->Accessories->Terminal:

For the FileSystem part, issue the command:

```
sudo fdisk -l
```

and look for the "Device" w/c has an asterisk (*) sign on it's Boot collumn, that would be your FileSystem. Then issue the command:

```
badblocks /dev/Device_with_asterisk
```

And check if it returns any error.

---

### Post by artisan on 2008-06-18
comp@comp-desktop:~$ badblocks /dev/sda1
badblocks: Permission denied while trying to determine device size

---

