---
title: "Help! I uninstalled the network manager- now I can't install anything!"
date: 2013-06-22
forum: General Help
---

### Post by itlarson on 2013-06-22
I uninstalled the network manager to install wicd, since wifi wasn't working.  Unfortunatly now I have no internet at all, and can't install anything.  How can I reinstall the network manager from the live cd?

---

### Post by hansdown on 2013-06-22
Hi itlarson.

A live cd will get you an internet connection, (a wired connection is best).

You can then open software centre, or synaptic, and install 

> netwok manager

Be sure to install the correct architecture; 64 bit, or 32 bit.

---

### Post by itlarson on 2013-06-22
screw it- reinstalling yet again.

---

### Post by hansdown on 2013-06-22
> **itlarson said:**
> screw it- reinstalling yet again.

You wouldn't believe how many times I reinstalled in my first attempts.

It gets easier.

---

### Post by 3rdalbum on 2013-06-23
If your wifi is not working, I doubt a different network manager will help. All network managers on Linux actually run a terminal command that starts the connection.

Sounds like you have a driver problem.

---

### Post by Yellow Pasque on 2013-06-23
You don't need network manager. It's one of the first things I get rid of on my non-mobile desktops (pointless bloat). Of course, then you need to get an IP address:
```
sudo dhclient eth0
```

---

### Post by itlarson on 2013-06-29
Thanks everyone for the replies.  Yes- I went off half cocked and reinstalled.  If I'd stopped and thought about it, I probably would have realized there is a way to get the network up from the command line, which would have allowed me to reinstall the network manager. 

Someone sugested installing the network manager from the live CD.  The problem is this doesn't presist after a reboot.  There is a way to make this work, though:  

sudo mount /dev/sda1 /media
sudo mount /dev/sda2 /media/home
sudo mount --bind /dev/ /media/dev/
sudo mount --bind /sys/ /media/sys/
sudo mount --bind /proc/ /media/proc/
sudo chroot /media
sudo apt-get install network-manager network-manager-gnome

Assuming sda1 is my root directory, and sda2 is my home directory, this will install the network manager to my installed linux instead of the ramdisk created by the live cd.

As for the wifi problem, this was actually caused by me mucking around in the bios.  The laptop I am working on is very old, and I was trying all kinds of things to maximise performance.

---

