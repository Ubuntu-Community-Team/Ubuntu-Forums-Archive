---
title: "upgrading to larger hard drive"
date: 2007-10-06
forum: General Help
---

### Post by caen1944 on 2007-10-06
Hi Folks,

Ran into an problem when trying to move my ubuntu installation from a 90 gig partition to a 450 gig one.

I did this.

-Booted from live CD and made image of my linux partition with partimage to usb drive
-installed new 500 gig drive, partitioned and installed ubuntu like normal, to get grub working
-checked new install, it works.
-booted from live cd and used partimage to restore the old data over the new partition from usb drive
-booted from the new drive, everything seemed fine except:

The new drive seems to have the same 90 gig size as the old drive. Also I was expecting the fstab to have the wrong UUID's, but they match what vol_id reports. How did that happen?

Anyway, the wrong filesystem size is really annoying. Gparted reports that I have used 370 gigs of my new drive, even though I have only used 17 gigs. 

After poking around the forums and the net, I find that both partimage and the dd command will leave you with a new filesystem that is the same size as the old one, which is rather unhelpful. I found some exceedingly complex instructions in the forums, but there must be an easier way to do something this simple and obviously necessary. Particularly for users that start with ubuntu on a small drive, get to like it, and want to move to a bigger drive.

Any simple solutions? I'll report back if I figure out a better way.

Thanks.

---

### Post by zvacet on 2007-10-06
[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by caen1944 on 2007-10-06
Here is something that worked to get me around the problem. Next time I'll follow the advice of the link provided by last poster though.

Booting from the live CD, I reformated my new large partition, and then used gparted to resize the partition to be the same size as my previous partition containing my ubuntu install.

Then I used partimage to restore the image from the old partition to my new one.

Finally, I used gparted again to make the new partition the full size that I wanted. Gparted reported an error at the end of its work, but fsck doesn't find any problem with the new partition and it boots and operates just fine. 

I am a little concerned about the gparted error, so maybe I'll keep my old drive for a while before I repurpose it. 

Kind of a round a bout way to do this, but it seemed to work.

Thanks,

---

### Post by dcstar on 2007-10-07
> **caen1944 said:**
> 
.........
Finally, I used gparted again to make the new partition the full size that I wanted. Gparted reported an error at the end of its work, but fsck doesn't find any problem with the new partition and it boots and operates just fine. 

I am a little concerned about the gparted error, so maybe I'll keep my old drive for a while before I repurpose it. 
........,

If you use Gparted for this and you still have the Gnome Automount options turned on, then you will get an error as the resized partition will be automatically remounted before Gparted can do the final fsck on it.

Chances are that there is no problem with your new partition/disk.

---

### Post by caen1944 on 2007-10-07
Thanks David,

Yeah, it automounted the partition. I didn't know that gparted was going to do a fsck on it, so wasn't sure what caused the error. Good to know.

So far it looks like it there is no problem. I am intrigued as to how the UUID's in my fstab are the right ones for my new drive though. Either partimage did this during the restore, or grub or the kernel edited this at first boot up with the new drive. 

Anyway, all is good. Thanks for the help.

---

