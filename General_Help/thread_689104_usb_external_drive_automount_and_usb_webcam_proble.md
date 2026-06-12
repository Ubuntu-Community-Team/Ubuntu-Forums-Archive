---
title: "usb external drive automount and usb webcam problems"
date: 2008-02-06
forum: General Help
---

### Post by bhrgunatha on 2008-02-06
I'm using kubuntu gutsy 7.10

1) I have an external usb drive (permanently connected to my PC) which I have added to /etc/fstab with the following:
```
/dev/sdc1 /media/usb-ext ext3 user,atime,auto,rw,nodev,noexec,nosuid 0 0

```

The trouble is it never mounts when I re-boot.
After rebooting it's fine if I type 
```
sudo mount -a

```

2) I have an old usb webcam which works beautifully except in skpe. I found the solution is to use gstfakevideo which needs the device to be /dev/video1 rather than /dev/video0 and that's fine, except that when I reboot the webcam device is at /dev/video0 again. Whenever I reboot I need to type in  
```
sudo mv /dev/video0 /dev/video1

```

I've tried a whole manner of things to run these 2 commands automatically when the machine reboots but the problem is they both require superuser privileges i.e. sudo.
The only thing I've managed to succeed is to add a script to ~/.kde/Autostart 
```

#!/bin/bash
echo <mypassword> | sudo mv /dev/video0 /dev/video1
echo <mypassword> | sudo mount -a

```

This seems a horrible kludge  and I don't like having my password in a text file - even though I'm the only user of the machine.

Can anyone suggest a better solution to run those 2 commands at startup?

---

### Post by geraldm on 2008-02-06
Try using a script that is run on booting /etc/init.d/rc.local
This script would be run as root, so sudo is not needed, and password need not be used.
Backup the file before making any changes.

Gerald

---

### Post by bhrgunatha on 2008-02-07
Thanks, but that  didn't work.

Although it did give me a good cue to read up about the boot sequence and the scripts in init.d and rcN.d's so I've learned something so thanks for that too.

I discovered a message in the system log saying the mount limit had been reached and I should run ex2fsck. I did that, but still no joy.

I've tried modifying rc.local to include those commands in the start) section - no luck.

I've tried putting my own script in init.d and using update-rc.d with several configurations including:
start 99 5 .
start 99 2 3 4 5 .
defaults 99
multiuser

As I can only test these by rebooting I've wasted hours on this and I'm no closer to fixing it or understanding why they aren't work.
Unfortunately I'm a linux n00b and I don't know  how to track down the problem(s).

Any pointers would be **very** welcome.

---

### Post by geo909 on 2008-02-07
For easy-configuring external usb storage devises, I use "pysdm"
(Python Storage Device Manager). You can find it in synaptic. It has a graphical interface. You choose the drive/partition you want and under "assistant" tab you can find options like "boot at startup" and other stuff.. You just tick them and you are ready (you have to reboot maybe). It has worked fine for me.

Hope that helps...

---

### Post by bhrgunatha on 2008-02-08
Thanks, I've pysdm and it's great for tweaking the config options in /etc/fstab, but it doesn't help solve my problem though.
The drive is set to automount at boot time already.

My theory is that it's something to do with them both being usb devices and somehow the usb subsystem is no longer working, but I can't understand why or how to track down the problem. 

I'm certain the drive has been mounted at boot time previously, maybe something is deferring usb operations during the boot sequence?

---

### Post by aparigraha on 2008-02-11
you could try to label your usb drives. had the exact same issue. but i solved it through labeling.

this thread got it all:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by bhrgunatha on 2008-02-12
Yes that's it!
I labelled my drive and now it's available after booting without  the need for any script.

I managed to work a solution out for the webcam based on what geraldm suggested. I finally noticed the /etc/rcS.d directory.
I had a look around in there and the README said 
> 
* After the S40 scripts have executed, all local file systems are mounted
  and networking is available. All device drivers have been initialized.

* After the S60 scripts have executed, the system clock has been set, NFS
  filesystems have been mounted (unless the system depends on the automounter,
  which is started later) and the filesystems have been cleaned.


So I put a script called move-webcam into /etc/init.d with 
```

#! /bin/sh 
mv /dev/video0 /dev/video1 

```

Then I ran the following:

```

sudo chmod +x move-webcam
sudo update-rc.d move-webcam start 99 S .

```

I thought that update-rc.d needed a number for the run-level (the last argument.)
After I tried it with "S" it put a link to my script in /etc/rcS.d and everything worked fine once I rebooted.

---

