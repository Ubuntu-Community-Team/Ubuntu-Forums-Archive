---
title: "Ubuntu won't use my whole hard drive"
date: 2007-07-17
forum: General Help
---

### Post by whtmgcwmn on 2007-07-17
Please help... I'm trying to make the three partitions suggested  - a swap and a boot, which were already installed bu my CD (I'm running dapper if it makes a difference)  and I want it to use the big space that's left for everything else.  I don't know how to do it, I've tried and tried.

Anyway GParted says
Partition              filesystem          size          used               unused           flags

/dev/hda1            ext3                   3.03 Gb    1.90GB           1.13GB           boot
/dev/hda2            extended            52.90GB       ------             ------
  /dev/hda6          ext3                 51.93GB       961.66MB        50.89GB
  /dev/hda5          linux-swap          1.07GB        ----------           ----------


All the partition except dev/hda/6 have the little lock next to them.  What's my next step?

---

### Post by bernied on 2007-07-17
Are you trying to do this from your installed system? If so, try it from the live-cd, and make sure all partitions are unmounted before doing anything.

Or is this a problem that you are having during install?

---

### Post by whtmgcwmn on 2007-07-17
I just installed it, and this is what it did.  I guess you can tell how many times I've tries since its up to hda6 now.  This is my second complete installation, the first time it ran out of space after I downloaded the updates and starting adding extensions to firefox.  That's the only way I knew something was even wrong.

---

### Post by whtmgcwmn on 2007-07-17
Actually, I think it's something I did during installation that I just don't know how to fix

---

### Post by le_jawa on 2007-07-17
I think bernied nailed it.  Those little lock icons you are seeing mean the partition can't be changed right now because they're mounted.  Boot from your live CD run GParted from there.

Oh!  And welcome to the Ubuntu forums, [whtmgcwmn]("http://ubuntuforums.org/member.php?u=343903")!

Jason

---

### Post by whtmgcwmn on 2007-07-17
Thanks for the welcome.  I restarted using the livecd, it took a really loong time, I got a couple error messages that I can't remember now, and now I'm at the gparted screen which shows the sames as it did before, except the first partition is not locked (hda1).  What should I do now, I want linux to use the rest of the hard drive as extra space, not the boot partition.

---

### Post by Jixxon on 2007-07-17
I have no idea what the cause of the problem is, but I have run into partition troubles after an install as well. For a solution I downloaded and burned the ISO for Darik's Boot and Nuke CD. I ran that and did a three pass wipe of my entire HD to get rid of any partition tables and data that might have been lurking and causing trouble.

From this point it is like having a brand new drive. You should be able to set up the partitions with gparted without error. After that is done the OS installation should go smoothly. I know it is kind of drastic to wipe the drive, but it works for me when I am at my wits end.

Good luck and welcome.

---

### Post by whtmgcwmn on 2007-07-17
Is tehre another way to erase the partition table?  I don't have a CD burner.

---

### Post by Jixxon on 2007-07-17
If you would like to go the DBAN route you can also load the program from floppy disks or a USB flash drive. Here is the link to the DBAN page - [http://dban.sourceforge.net/]("http://dban.sourceforge.net/") - The download options/links are listed at the very top of the page.

---

### Post by whtmgcwmn on 2007-07-17
Dumb question - how do I get my computer to boot from USB?  My options are floppy, CD, or HDD.

Thanks for your help.

---

### Post by g2g591 on 2007-07-17
the lock indicates those partations or drives are mounted, in order to unmount them right click them and click unmount, then you are free to resize them as you wish. That way you won't have to wipe your drive like the others suggest.

---

### Post by Jixxon on 2007-07-17
There is no such thing as a dumb question. The best way to learn anything is to ask :) 

I am assuming that you are checking your boot options from your bios. If USB is not listed then it is not an option. If that is the case I think I can safely assume that this is an older machine or at least an older mobo. 

You could check to see if there is a bios update for your motherboard, but that is getting into totally different area. I also assume by your response that the floppy disks are not an option. I am not sure where you can go from here (at least with the DBAN option). If you still want to try this maybe a friend has a burner to get the ISO to CD.

In a different direction... I don't know how far you want to go and what resources you have available, but there are other possible options with pulling out a PCs hard drive and using another machine to work on it.

You might want to try gparted again and check out all the possible partition delete and reformat settings/functions that are available. I know you probably have already done that, but I thought I would mention it. If none of these options work hopefully someone else has a different idea on how to fix this.

---

### Post by Jixxon on 2007-07-17
g2g591 is correct about the mounting information. My apologies - I misread your post and thought you tried that already... I was taking you in a whole different direction.

---

### Post by whtmgcwmn on 2007-07-17
I've tried the user guide, and I can't get it to mount in the first place.  How do you mount a logical partition?

---

### Post by Jixxon on 2007-07-18
Have you had any luck with this issue since yesterday? If I am not mistaken the mount option should be in the same menu as the unmount option (through the process that was mentioned in a previous post). If that doesn't work then something else is going on. Maybe my first bit of advice wasn't to terribly off.

---

### Post by wolfen69 on 2007-07-18
if you are just trying to use the whole drive for ubuntu, boot live cd-install-when you get to the partitioning part choose-"guided/use whole drive". done.

---

