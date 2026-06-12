---
title: "Can't boot CD in VMWare"
date: 2006-11-16
forum: General Help
---

### Post by ImNeat on 2006-11-16
I am unable to boot an installation CD through VMWare, because it seems to be unable to detect my CD-ROM.
I get the following error when I "Power on" the virtual machine:
```
CD-ROM: '/media/cdrom0' exists, but does not appear to be a CD-ROM device.
Virtual device ide1:0 will start disconnected.
```

Which is strange, because /media/cdrom0 is where my CD-ROM drive is mounted.

I am running Ubuntu 5.10 & Gnome.  Any help will be much appreciated.

---

### Post by bulldog on 2006-11-16
How many cd-rom device do you have?

If you have more than one,just try the other one,you can be lucky,like I was when I had the same issue.

---

### Post by ImNeat on 2006-11-16
I have two CD-ROM drives - one is mounted /media/cdrom0 the other /media/cdrom1.  VMWare doesn't like either of those mount points for whatever reason.  Does Ubuntu mount your drives there?  If so, what do your VMWare CD-ROM settings look like?

---

### Post by mbeierl on 2006-11-16
Slight point of clarification:  

you have to remember that VMWare is pretending to be an operating system.  As such it does not want the "folder" where the CD is mounted; it wants access directly to the raw device: /dev/cdrom typically.

If it's not, look in /etc/fstab for the /media/cdrom entry.  It should look something like this:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
In this case, the device for /media/cdrom is /dev/scd0.

Hope this helps! :)

---

### Post by ImNeat on 2006-11-16
**mbeierl**, you're absolutely right.  I can't believe I didn't pick up on that myself.  /dev/hda did the trick... much much thanks!

---

### Post by A_608 on 2006-12-14
Hi, 

I am having the same problem in Edgy.  No access to the cdrom.  
In Edgy /etc/fstab doesn't exist. Has anyone found a solution for this in Edgy?  I am running 98SE as a virtual machine. Until windows sees the cdrom, I can't load the video drivers that I need.

---

