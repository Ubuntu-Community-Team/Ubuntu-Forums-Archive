---
title: "New Installation + Existing RAID 5"
date: 2007-12-18
forum: General Help
---

### Post by Joshua on 2007-12-18
Well, I had everything running smooth on my new Gutsy + RAID 5 box, but then all of a sudden it wouldn't boot.

First, some basics about my system.  I have an 80Gb drive for the OS (all of /home, /boot, swap, etc.).  The RAID is a separate block of drives that was mounted at /mnt/share.  I'm running Gutsy for AMD64 and have mdadm setup to keep the RAID 5 going.

I can only figure that the problem was caused by an error when trying to hybernate.  One evening I had a lot of stuff on the workspace that I didn't want to rearange after a reboot.  So I tried to hybernate instead of shutdown in the evening (I'm trying to be more "green").  It seemed to be taking a while so I moved the mouse.  The screen-unlock window popped up, and since I was getting impatient, I entered the password and then went in and shutdown the system.

The next morning, the system hung really early in the bootup.  I can't remember exactly what kinds of errors I got, but they indicated to me that there was a problem loading some kind of image from swap.  I assumed that the image was part of the hybernate process and that I messed it up by not waiting long enough the night before.  I couldn't get it to work so I reformatted the swap space and then tried to edit /etc/fstab to use the right partition.  At that point I couldn't save the file because nano kept saying that the file system was mounted read-only.  I tried to do the same with with gedit and a live CD.  That looked like it worked, but when I rebooted, it looked like it was still looking for an image somewhere.  At that point I gave up.

That brings me to my first question.  Anyone know what heppened here and how to prevent it?  Does this need a bug report?  (Of course I'm not sure if I can, or even want to recreate it in order to get some details about it.)

It was a new install so I just reinstalled everything, the 80Gb drive was really loud anyway, so I found another one and and did a fresh install of Gutsy.  Now everything looked good, until I added mdadm.  Remember, I already had several disks hooked up that were configured for RAID.  After adding mdadm, on boot it looked like mdadm got confused or something and dumped me into something called BusyBox.  This was regardless of whether I tried to re-assemble the existing RAID 5 array or not.  BusyBox looked like being at a shell prompt with a limited set of options.  I found some descriptions of other peoples' problems through Google that seem to be similar to mine, but I can't understand the solutions they describe, and the bug reports seem to be saying that this is fixed.  Anyone know what I can do about this?

---

### Post by fjgaude on 2007-12-18
Hello, Joshua! Good to see you back but really, not in this condition.

When you installed the new drive did you use the same controller slot?

I'm sure the array can be assembled with the new install of the OS. We have to figure out how to do 

```
sudo mdadm --assemble --scan --verbose
```

from whatever command line you can get. I suppose the new install doesn't see the mdamd.conf file, and if it does something is wrong with it.

Have you tried to use a LiveCD to mount the raid5 array?

---

### Post by Joshua on 2007-12-18
Well, here's the thing - it deffinately shouldn't see the mdadm.conf file because that's in /etc (or maybe /etc/mdadm).  I'm using a whole new drive, that has been newly formatted.  So it shouldn't exist anywhere right... although, maybe mdadm creates it as soon as I install it?  It could be creating a bad file.  But on top of that, I'm installing the OS to a different drive that's not part of the array.  I would think that any error with loading a RAID or using mdadm would be kept separate from the OS.  That was part of the reason that I wanted the OS on a different drive, rather than installed on the array.

I did connect the new drive to the same controller.  It's the IDE1 controller in the slave position.  (Shared with a CDROM as master.  I know it's not ideal, but I don't think that drive needs to be very fast.  Almost all of my data would written to and read from the array.)  I left all the other drives in the same positions as well, and I'm pretty sure that they wouldn't change identifiers under Linux.  They never have in the past as long as they were connected to the same controllers.

As far as mounting.  I haven't tried to mount with a Live CD yet, but I did try to mount as soon as I installed mdadm once.  ie. I installed mdadm and set up the array, prior to restarting the computer.  I checked it with /proc/mdstat, and mounted it.  It looked good (though I only looked to see if the files showed up in Nautilus).  But on restart, it did the same dump into BusyBox.

I'll try the LiveCD later tonight.  It looks like dinner's about ready.

---

### Post by Joshua on 2007-12-18
By the way, it's good to see you again, too.  Up until this point everything had been working really well.  Had MythTV set up, playing music, watching TV.  Totally sweet with 1TB of space.  Thanks for all the help.  I was planning to write up some details about what I did, until this happened.

---

### Post by fjgaude on 2007-12-18
Okay, I think I understand... I've not had such a problem with the things I've done.

Even though the OS is on its own drive the mdadm.conf file is placed in the /etc/mdadm directory that mdadm made when you installed mdadm.

The times I've changed OSs or motherboards, all I did was the sudo mdadm --assemble --scan --verbose thing and my array was working as it should. I then placed it in the fstab file and that has been it.

Gutsy seems to not care about changing drive names like Feisty did, so we should be okay from that standpoint.

I don't know other than to run that assemble command. Or any of the or query or display commands. The busybox might have enough command capability to somehow get you to at least get into the OS, and from there you should be able to do the assemble. Still it seems Gutsy should have assembled it automatically. I guess it's the change in OS, now new that is the issue.

Maybe someone else has suggestions. Please!

---

