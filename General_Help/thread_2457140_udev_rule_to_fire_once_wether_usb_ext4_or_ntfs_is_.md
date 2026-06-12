---
title: "udev rule to fire once wether usb ext4 or ntfs is plugged in"
date: 2021-01-26
forum: General Help
---

### Post by franknfurter2 on 2021-01-26
Hello,

I'm new to udev rules but did understand a lot so far. I get a rule working but now I get stuck. What is my goal? I will run a headless system and each time I plug in a USB device a udev rule should start a script to copy some files from the system to the usb drive. I want this to work for each kind of usb device and partition type I plug in. So for testing purpose I use a ext4 sdcard in an sdcard-usb adapter and an ntfs formatted usb stick.

My udev rule is like this at the moment:

ACTION=="add", SUBSYSTEM=="block",ENV{DEVTYPE}=="partition", RUN="/home/frank/hello.sh '%E{DEVNAME}'"

Problem is that this rule works for the usb stick with ntfs partition that ends up as device /dev/sde1. This rule does not work for the sdcard-usb adapter. udev does not produce a partition DEVTYPE in that case.
When I ommit the devtype, the rule fires twice for the USB stick (first with DEVNAME /dev/sde and second with DEVNAME /dev/sde1) and once for the sdcard-usb adapter.

What I need is a rule, that fires once.

Do you have any guidance?

Regards

Frank

---

### Post by TheFu on 2021-01-28
a) never trust that the device names are fixed.  They are not.  sde isn't guaranteed.
b) ignore any rules that don't include the partition number.
c) place an empty file on the storage that means "I haven't done anything automatic yet", then as part of your processing, only do automatic steps when that file exists. If it doesn't exist, ignore.  This is a very common technique used to validate a mount has happened, especially when backups are involved.  But you probably have realized that not all storage mounts are the same. If a GUI is involved, it is very possible that a fake mount is used which has real impact to performance of that storage.

---

### Post by franknfurter2 on 2021-01-28
Dear TheFu,

thanks for your advice, but I think I have not understand all of them:

a)
Yes, you are right, never trust device name. So that's the reason why I'm passing it to the script hello.sh via parameter.
b)
When I plug in the sdcard-usb adapter it results in a device /dev/sde and gets mounted by ubuntu. Here is the output of lsblk -f in that case 
"sde    ext4     data     4688f482-a18b-440e-b7bf-121d4326b66e    6,8G     0% /media/frank/data"
So there isn't a partition number and so I should not use this adapter. Is that, what you mean? If so, the problem will not arise because then one can use the ENV{DEVTYPE}=="partition" predicate in the udev rule.

c)
It's a good idea to place a file on the device to control automatism. But what do you mean with "fake mount". What is this? Never heard that before.

Regards

Frank

---

### Post by TheFu on 2021-01-28
Ok .... so I'd not really use the udev method.  I'd use autofs with automounting.  This is an on-demand mount thing. It uses real mounts, not fake mounts.  The summary about that is - either a mount shows up in the mtab or it doesn't.  Fake mounts do not.  Depending on which release you use, gio or gvfs or udisks could perform fake mounting.

automounting can be tied to UUIDs or LABELs.  I use LABELs since humans understand those more clearly.  Also, storage that doesn't have partitions can still have a LABEL and the real-mount can still be caused.

dmesg output includes storage information based on udev.  This can be monitored ... or you can use **inotify** /dev/disk/by-label/* so that whenever a new device shows up, then you can try to access the pre-configured automount storage location, and do whatever it is you like if it is there.  This is basic shell scripting, though the inotify stuff does add complexity. [https://www.linuxjournal.com/content/linux-filesystem-events-inotify](https://www.linuxjournal.com/content/linux-filesystem-events-inotify)

Is it fine if the action is delayed 1-2 minutes? That would make thinks 10x easier.

I'm not a fan of screwing with udev for this sort of thing.  If it was a good idea, wouldn't there be plenty of how-tos already?

---

### Post by franknfurter2 on 2021-01-28
Dear TheFu,  

maybe I was using udev rules because of a training course I'm doing to better understand Linux. But it seems that you opened my eyes that there are better solutions to my problem.

**inotify** sounds good, but I don't think I have the required knowledge of shell scripting at the moment. I have a better understanding of Python so I have to decide which path to go from here.  Thank you for putting up the direction sign.

Regards

Frank

---

### Post by TheFu on 2021-01-28
I bet python has an inotify module.

Not sure if what I've suggested are "better."  That is something only you can answer.  Definitely more well-used, however.

---

