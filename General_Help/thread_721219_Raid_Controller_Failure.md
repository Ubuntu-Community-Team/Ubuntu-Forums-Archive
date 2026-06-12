---
title: "Raid Controller Failure"
date: 2008-03-11
forum: General Help
---

### Post by seffyroff on 2008-03-11
I'm in a bit of a pickle.

My old fileserver (running SuSE 9.2) just lost its RAID controller card.  It's a simple cheap PCI IDE RAID Card configured as a Mirror for two drives.  I'd like to recover the data from the raid somehow, possibly using my lovely Ubuntu box, but I am unsure how to proceed.

Here's what I've tried:

I can get the old fileserver to boot with the RAID card sometimes, and currently I have it running with a USB disk plugged in, copying the data off.  Two problems with this: I think the RAID controller has failed back to some sort of compatibility mode, AND the fileserver itself being quite old only has USB1.  I started copying last Friday evening and it's still copying the first subdirectory of around 80GB today.  The total data size on the array is 200GB :(

Is there another way I can recover this data in a more robust fashion?  I have bought a new RAID Controller card (not the same make or model unfortunately) - is it possible to plug the disks into the new controller in my Ubuntu machine maybe? or just swap the new controller into the Fileserver?  I am concerned that if I connect the new controller to the disks it'll somehow initialize them and I'll lose my data.

Or is there a really simple solution, like just connecting the drives directly to a regular IDE interface and getting the data without any RAID shenanigans?  The filesystem of the RAID is RieserFS.

---

### Post by justleen on 2008-03-11
Most likely you will not see any data when connecting them to an IDE port.

YOu will have to rebuild the raid, with the old raid controller. There is a small change the new controller will pick it up, but i dont think so..

I'd say try to get the old raid card to work in you new system, hook up the disk, and see what the RAID bios gives you for options.

---

### Post by seffyroff on 2008-03-11
Tried just plugging it into my Ubuntu box's IDE interface.

fdisk displays the partition type as 'Linux raid autodetect' rather than Reiserfs.

I'm stumped on how to proceed from here.

---

### Post by seffyroff on 2008-03-11
A couple of clarifications:

I don't know exactly how the RAID array was set up.  I didn't set it up.  It appears to be Striped on the controller card (the filesystem was a capacity of ~230GB. There are two 120GB disks connected to the controller).  There appears to be a software raid within that.  the mount point of the filesystem was something like /dev/md0 IIRC.  

Is it normal to have a hardware raid with software raid on top of it?  Or was the guy who set it up crazy?  Or am I just reading it wrong and that setup isn't possible?

Also: The RAID itself is still intact.  The data is there if I can get the machine to boot with the controller working.  There's no problem with the data integrity, it's only the controller itself which has failed.

---

### Post by fjgaude on 2008-03-11
Well, with a mountpoint of /dev/md0 this is software raid using mdadm.

The controller is not in raid mode, and likely is just being used as that, a controller for the two drives.

You can use an mdadm command, after you have installed mdadm, like this to assemble:

```
sudo mdadm --assemble --scan
```

That will do it.

---

### Post by seffyroff on 2008-03-11
Thanks for your reply.  That did the trick (and thanks to my mate also for pointing this out).

The RAID card was indeed just providing IDE function, that's what threw me.

*blood pressure returns to normal*

mdadm is really a great tool for RAID :)

---

### Post by fjgaude on 2008-03-11
Read the man pages, man mdadm, for more details. And here's how I learned it from long ago:

[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

It is a great tool, mature too.

Glad you got your blood pressure down... now is the time to backup all important data, eh?

---

