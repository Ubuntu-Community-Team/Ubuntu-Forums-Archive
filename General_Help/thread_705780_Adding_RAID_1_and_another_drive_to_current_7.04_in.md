---
title: "Adding RAID 1 and another drive to current 7.04 install"
date: 2008-02-23
forum: General Help
---

### Post by free beer and brats on 2008-02-23
Hello all!

I'm not a ubuntu noob (i've got it on like 5 computers for the past 2 years), but I need some advise on this RAID question...  I've got an old BOXX blade server with an intel board.  The OS is running off a small (9.1GB) SCSI drive on SCSI channel A, and I have a 250 GB IDE ATA storage volume on the primary IDE slot.  Here's the question: is it difficult/possible to add another IDE drive onto the same cable that the current 250 GB drive is sitting on, and then have the two set up in a RAID 1 array?  Would I have to (re)format both drives to accomplish this?  One drive has 40GB worth of data on it that I would prefer not to have to shuffle around...  I would just like to add the drive and have a mirrored situation so I don't have to worry about data loss.

Do I need an IDE card to do this?  Can they run together on the same cable OK?

What is the best software to run a soft RAID 1? mdadm?

I've searched around the forums and I can't find any answers to my specific situation.  Any help will be much appreciated...  Plus I figure now that I've actually registered for an account I can answer all the questions I frequently read... ;)
 
Thanks!

---

### Post by fjgaude on 2008-02-23
For Linux software raid, mdadm is the way to go.

I've not done it but I feel it is possible to do what you want, a raid1 array with both drives on the same IDE parallel cable.

Here's the command to start the process:
```

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/yyy missing
```

where the /dev/yyy is the drive that's new without any data on it. The missing will be added later after all its data is coped to the created raid1 array.

Now format the array like so:

```
sudo mkfs -t ext3 /dev/md0
```

Make a mount point for the array, like so:

```
sudo mkdir /media/raid
```

or you could mount off of your /home directory:

```
sudo mkdir /home/yourplace
```

Now mount the broken array, because it is not complete yet:

```
sudo mount /dev/md0 /media/raid
```

or wherever you have chosen.

Next, copy all the data on the missing drive to the array. Just drag and drop using Nautilus or

```
cp /dev/whatever /dev/md0
```

Now add that whatever drive into the array:

```
sudo mdadm /dev/md0 --add /dev/whatever
```

And wait for it to sync up, using:

```
watch cat /proc/mdstat
```

Now I trust you will read and study the man pages for mdadm, before you attempt the lengthy process. If you have questions let us know.

Hppy raiding. <smile>

---

### Post by free beer and brats on 2008-02-27
Hi, thanks for the detailed response!  I have the drive now, one other question.. should the jumper be set to 'slave' on the drive I'm adding?  

I will post the results of this as soon as I'm through (or when I am hung up!).

Thanks again for the reply.

---

### Post by fjgaude on 2008-02-27
> **free beer and brats said:**
> Hi, thanks for the detailed response!  I have the drive now, one other question.. should the jumper be set to 'slave' on the drive I'm adding?  

I will post the results of this as soon as I'm through (or when I am hung up!).

Thanks again for the reply.

Well, I would think so, if you have another drive as Master. I don't use other than SATA these days, but go the 'slave' route. That is the only option you have, eh?

OTOH, what about the type of IDE cable you are using? Is it the kind that takes care of the master/slave routing?

Have studied the man pages for mdadm?

---

### Post by doublehelixer on 2008-02-27
Be aware that if you put both raid drives on the same IDE bus you will take a significant performance hit.  If at all possible you should try to get the mirrored halves on separate IDE busses.

---

### Post by free beer and brats on 2008-02-27
Hi.  I went with the configuration that seemed logical... one master, one slave.  After I thought about it a bit, and manned around, I don't think mdadm will care.  

I'm formatting now, we'll see how it goes though.

As per speed... do you think it will be significantly slower than a single drive on that bus?  This is a scsi board (but I can't afford huge scsi drives, and a SATA card wont fit in the 2U case) so I'm stuck with old IDE, and I only have 2 IDE channels (one is occupied by the CD drive).  If it will run at about the same speed as a single drive on that channel, I think I can live with that.  Is it possible/would it be faster to have one drive running off the second port of the other IDE channel (as a slave to the CD drive, on a better cable)?  I'm not really doing this for speed as much as for data integrity.

Thanks for all the input!

---

### Post by fjgaude on 2008-02-28
A SCSI board? Interesting... yes, I understand, going back to read your first post.

Since the raid is going to be mirror type I think you will be okay going with the master/slave route. As for speed, it depends a lot of the drives themselves. How fast are they? Likely in the 50-70MB/sec range as measured by hdparm.

```
suod apt-get install hdparm
```

```
sudo hdaprm -tT /dev/hda1
```

Or whatever your drive is called. After the array is completed you can do it on /dev/md0, if that is what you end up calling your array.

Go for it... but don't forget to use that "missing" label when you set up the drives with mdadm. You have to format the array then and that destroys all the data. Then copy from the present drive that has all the data to the array which has really only one drive in it. After that, add the original drive to it.

Good luck.

---

### Post by free beer and brats on 2008-02-28
Well...  I've made a fine mess of things now!  I was in the middle of synching the devices (which was 26% done after 8 hours, that can't be normal, can it?) and I hit a fatal error and she froze.  This was not a huge surprise to me, so I rebooted, and figured I'd take this opportunity to rearrange things a little bit (since it seemed slow on one IDE bus). 

I rebooted and knowing that mdadm would load at boot and attempt to synch up the drives, I killed the processes and proceeded to uninstall mdadm so I could make some configuration changes, with the following: 
```
sudo apt-get --purge remove mdadm
```

And when I checked around, it looked like it had removed the config files... Now I shutdown to install a PCI IDE card and hook the two 250 GB drives to that.  When I rebooted, everything seemed fine, so I refreshed my backup and wiped the drives to do a clean RAID1 setup off the PCI 66 bus, with sepparate cables. 

However, when I ran ```
sudo apt-get install mdadm
``` I find that its already installed!  I look at my active processes, and then run ```
watch cat /proc/mdstat
``` to find that mdadm is trying to resync the devices... and its found them in their new locations!

Now I feel like a real amature (which, of course, I am)  I kill it again and try to force uninstall it, where it hangs.  When that finally dies, the system is very buggy... so I try to restart, and here I am...  

It gets through grub to where it queries the root partition to take over, at which point it hangs indefinitely, or dumps me to busybox.  Do you think my init is hosed?  I'm having trouble even booting to a CD now, but if I could, do you think I could recover/fix the boot drive?  I'm going to try booting to the CD without the PCI card and drives hooked up.

I would rather not freshly install, if i can avoid it.  Thanks for all your patience, I went from a solidly running box yesterday to a pile of fans and hardrives that wont even boot to a CD today... 
Morgan

---

### Post by fjgaude on 2008-02-29
I hear you man, I do think with a lot of work you will get back to where you were. I have to run now but will get back with you when I get back to the office.

Keep the chin up.

---

### Post by free beer and brats on 2008-02-29
Hi Frank, 

Thanks! I appreciate all the help.  I had issues getting this box to boot from the CD when I first installed, but after retrying about 8 times, it would boot.  Now it doesn't seem to want to boot at all. I get "cannot display video in this mode," which is where the "ubuntu" logo and track bar are... it will sit there indefinitely.  I got that when I installed, and when I booted the machine before the issues, I also got the "cannot display video this mode", but it would procede.  Should I try the alternate install?

Is there a way I can bootstrap the root partition up with the CD?  Something like that sounds familiar, but I have not yet found one that will do what I need.  Do you know what md does to the init or boot loaders on the drive itself?

Thanks again,
Morgan

---

### Post by fjgaude on 2008-02-29
Well, one thing to try, is to simply disconnect the new drive you added and see if the boot occurs.

By adding a drive the drive letters are likely changed. One way out of this is to use only UUIDs for drives, which any late issue Ubuntu does for the boot drive. But adding another drive after the install likely has that drive using its name, e.g., hdb1.

As for md in the kernel, it knows that raid is being used and looks into the mdadm directory to see what is to be assembled. It doesn't do any assemble through. You have to have that in your fstab file.

At this point I can't say what condition the two drives of array are... since you stopped the sync.

What computer CPU, its speed, what video board? What version of Ubuntu?

---

### Post by free beer and brats on 2008-02-29
yes, I disconnected the drives, and attempted to boot... to no avail.  From the looks of things, GRUB is looking for a bootable partition on the UUID that must be my SCSI drive (with the OS installed on it) (I get this from trying to  boot using the recovery/safe boot GRUB option).  It was the only drive identified by UUID when I looked at my fstab and mtab yesterday afternoon.  GRUB finds the drive bootable, but it looks like the drive cannot proceed with the boot because its missing some module or line in the boot file...  What else about init[xx] does mdadm change?  I thought it was just called to start at boot and was not critically involved in the boot process (since I am not booting from the RAID drives themselves).  I get a "waiting for Root partition" message, at which point it hangs for a while, and then it dumps me to a busybox terminal.  Is there anything I can do at busybox?  Can I get this thing up and running and repair the boot portion of the root partition?

This is an Intel L440GX+ motherboard with dual P3 733 CPUs and integrated onboard video (of dubious quality).  I am running ubuntu 7.04.  Thanks for all the help.
Morgan

---

### Post by free beer and brats on 2008-02-29
The last few lines of the recovery boot are:

Begin: running /scripts/init-premount ...
Done.
Begin: mounting root file system ...
Begin: running /scripts/local-top ...
Done.
Begin: Waiting for root file system ... ...
Done.
Check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-UUID/ 0d25ac09-blablabla...  does not exist.  Dropping to a shell!

Busybox


Does that mean its able to mount the root partition and can't find the necessary boot procedure from there, or that it can't be mounted?

---

### Post by fjgaude on 2008-02-29
To me it means that the device with that UUID doesn't exist.

Here's what you can do: Boot from LiveCD. Get to a command line and check both the fstab file and the menu.list file.

After that do something to find out what the boot disk's UUID is and compare with what's in the menu.lst.

You know what the three boot lines in menu.lst look like?

---

### Post by free beer and brats on 2008-03-01
Hi Frank,

Thanks for all the help, I'll update this as soon as I can get it to boot from a CD...

---

### Post by bbarrons on 2008-03-02
Have you tried to boot over the network yet with pxe?

---

