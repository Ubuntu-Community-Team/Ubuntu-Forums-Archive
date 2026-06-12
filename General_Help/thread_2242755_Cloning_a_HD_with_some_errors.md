---
title: "Cloning a HD with some errors"
date: 2014-09-03
forum: General Help
---

### Post by russ3 on 2014-09-03
I made a post recently about some errors I've been having with my HD - at random, I would get messages that I did not have permission to read/write to my drive - and all my folders had little locks next to them.  If I tried to reboot, I wouldn't be able to - with the Ubuntu liveCD installed, I frequently wouldn't even be able to mount the drive.  With a combination of running FSCK and/or restoring a backup superblock, I could get everything back to normal.  And the system is ran fine for 10 days, crashed again but has been running fine since...at first, I decided I'd just press my luck since I'm pretty broke, but common sense prevailed and I got a new drive.  Also forgot to mention, the HD SMART diagnostics showed 10 bad sectors, and failed the self-test I did on it - and switching ports, cables, etc didn't help at all.  Definitely a drive on the way to the grave.

I thought cloning the drive might be the best route to go - since this drive is all updated, and everything I installed how I like it, etc.  I decided to use Gparted as shown in this guide.  [http://ubuntuforums.org/archive/index.php/t-302717.html](http://ubuntuforums.org/archive/index.php/t-302717.html)

This is what fdisk shows on the old drive

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3891300351  1945649152   83  Linux
/dev/sda2      3891302398  3907024895     7861249    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3891302400  3907024895     7861248   82  Linux swap / Solaris

Picked up a Seagate 3TB drive (old drive was a 2TB) and got it recognized by my BIOS , and by gparted no problem.  It took 12 hours or so (the read rate kept getting lower and lower....) but I copied sda1 over to the new drive and also increased the partition size since the new drive is bigger (left some spare space for the swap).  I was unsure if I was supposed to copy sda2 and sda5.  I was able to copy sda5 , but not sda2 (and I couldn't figure out how to create a new Extended partition to put sda5 in).  During the copying of sda1 I did get some short read errors on some blocks - presumably the ones with bad sectors.  

Disconnected my old drive, and tried to boot from the new one.  Like the guide predicted, it didn't boot, so I booted from the Ubuntu 12.04 liveCD.  Was happy to see the partition had copied over and was able to be mounted (though it mentioned some files my be unreadable) - I could look at the directory structure, but told I didn't have permission to view the contents when I tried.  My problem came when I followed the instructions on creating a new GRUB - I ran 'sudo grub' from terminal as suggested but just got a message that the command 'grub' was not found.  Tried another page's advice on restoring GRUB to a newly cloned drive, and failed with that as well.  Also, in Gparted, I noticed the drive was not set as a boot drive , so I added the flag myself, but that did not help.

Got a bit tired of experimenting myself, and just hooked the old drive back up, and disconnected the new one - which now just has a clone of sda2 on it.  I don't have a lot of knowledge so any help is appreciated.  

My options seem to be (in order of preference)

1 - Figure out a way to make that cloned drive bootable (Is it possible that one of the blocks that had a short read was the superblock, and I should try restoring from a backup superblock on the new HD - with hopefully no more problems since the new drive seems to pass all SMART tests fine) - any other ideas to make this work would be very welcome...since I hate to have to run a dying HD for another 12 hours straight if I can avoid it.

2 - Erase the data on the new drive, and clone via a different method.  I'm thinking dd_rescue might have been more appropriate for my situation?  Any ideas on a better way to do it?

3 - Just install Ubuntu fresh on the new drive and copy over as many files from the dying drive as possible.  That sounds simple enough, but would I even have permission to copy those files?

thanks to anyone who read all this and has any suggestions!

---

### Post by Colin_Deisenroth on 2014-09-04
If I was you, I'd do a fresh install on the new drive, hook the 2nd drive up as a slave, and copy as much important data as possible using rsync (using root if needed). I used rsync to do this, and every time it got to a file or directory it couldn't copy, I would ctrl-c and put a --exclude for that file and it would skip it.

This is pretty close to your option #3 so I know it wasn't your best choice, but at least you'll know you have a clean, non-corrupt install of linux that won't randomly have errors and bugs, and also I think this will be the least time consuming and frustrating method as you'll have a working computer on a new drive to use while you slowly get data off your old drive.

If you have a laptop you can hook the 2nd drive up using a USB to Sata device that costs like $10-20.

---

### Post by russ3 on 2014-09-04
Thanks for the reply, I messed up around with the first option yesterday and couldn't get it to work...got to the point where I could install GRUB - but it seems to have trouble because the disc was GPA partioned and there wasn't room for Grub?  After messing around with it, I got frustrated and erased everything on the drive.

Your solution sounds good as a last resort, I think i'd going to try the Ubuntu Rescue Remix live CD next and use GNU DDrescue (though this sounds like it may give me problems using th entirety of my new drive?) - I'm really hesitant to give up on it,  because I had errors over a year ago...and the system continued to run fine for a long time.  And it still works fine now if I reconnected that drive.  Don't have a laptop or other system I can use in the meantime.

It is a bit frustrating, but figure at least I'm learning some new skills along the way!  Any other tips more than welcome, gotta get to work before I attempt to do anything.

---

### Post by russ3 on 2014-09-06
GNU ddrescue seems to be working albeit very slowly.  When it gets to an error, it becomes ridiculously slow unless you cancel and run it again (it picks up where it left off).  Thought i was good til towards the end when it was one error after another.  Storming bad here so just powered down and checked if the old drive could still boot.  It does.  Will try to finish with ddrescue tmrw when i have time to keep an eye on it.

---

### Post by russ3 on 2014-09-07
Finally got this to work!  Used Clonezilla (with the rescue tag enabled) to copy the data - then needed to use Boot Repair Disc (to purge the existing grub and then put on a new grub) to make it actually boot up.  Still have 1TB of my new 3TB drive unallocated - not sure I wanna mess with Gparted now that I got things working.  One strange thing - when my system boots up now - i get six errors says "Device Not found" or something similar , then it goes to the GRUB menu and everything seemingly works fine from there.  The SMART diagnostics show that there 84 bad sectors read during the cloning, hopefully that bad/missing data is somewhere relatively unimportant.

---

