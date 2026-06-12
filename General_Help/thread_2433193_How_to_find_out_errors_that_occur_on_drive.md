---
title: "How to find out errors that occur on drive?"
date: 2019-12-15
forum: General Help
---

### Post by askar-andersson on 2019-12-15
Hello!

I have the following in my /etc/fstab


```
UUID=7dd0c250-e210-48f5-9eba-dca33deac6ab /media/usb    ext4 user,errors=remount-ro,auto,exec,rw

```

Sometimes I find that the drive has become read-only (since I have remount-ro).

How can I find out what type of error occurs that results in the remount?

---

### Post by TheFu on 2019-12-15
First, the fstab is incorrect. It is missing 2 fields at the end.  Those should probably be **0   1**

For checking a file system for logical issues, use **fsck**.  One of those last 2 missing numbers in your fstab controls how often fsck is run automatically. 
For checking what the disk knows about itself, use **smartctl**.
For doing deeper, direct, tests, use **badblocks**.

These are not GUI programs.  You'll want o search for a tutorial on the use of each BEFORE attempting.

If there is any belief of **any** issue at all, the first thing should be to make a backup of anything you can't lose. Sometimes the only warning provided before total failure is similar to what you've experienced.

What type of USB storage is this?  If flash, running some of those commands is worse for the lifespan than just formatting the storage again and starting over.  If it is an SSD, there are some considerations. If it is a spinning disk, go crazy.

---

### Post by askar-andersson on 2019-12-16
Thank you!

I looked up the 0 1 thing, and found that the second number "[COLOR=#333333][FONT=Ubuntu]Controls the order in which [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]fsck[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] checks the device/partition for errors at boot time. The root device should be 1. Other partitions should be 2, or 0 to disable checking." As it is an external drive, perhaps it should be 2?

I have tested the disk with fsck and badblocks, and it found no errors.[/FONT][/COLOR]

It is a spinning disk, Seagate Expansion Portable Drive 4TB

---

### Post by vanadium on 2019-12-16
Indeed, make it "2" such that it is automatically checked on reboot after system drives have been checked.

---

### Post by TheFu on 2019-12-16
With systemd handling file system mounts the last few releases, the number doesn't matter - either it is 0 or non-0.  Yet another thing the systemd team decided to change, but not actually follow what previous commands did.

The manpage for systemd.mount and  systemd-fstab-generator explains.

```
       The passno field is treated like a simple boolean, and the ordering
       information is discarded. However, if the root file system is checked,
       it is checked before all the other file systems.

```

---

