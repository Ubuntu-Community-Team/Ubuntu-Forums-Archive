---
title: "Using Gparted to expand existing partition"
date: 2015-09-29
forum: General Help
---

### Post by Ace_Rimmer on 2015-09-29
Hi I'm having trouble getting my partitions fixed.  I have sde1 as my root partition and I shrank it down in size since it was way too big.  I want to add that space to sde5 which is my home partition.  But it seems that adding in space before an existing partition is tricky in Linux.  I've attached the picture of the gparted window but I can do this via CL if necessary.[ATTACH=CONFIG]264739[/ATTACH]

---

### Post by deadflowr on 2015-09-29
I'm guessing you created that /dev/sde3 partition and gave it a ext4 filesystem type?
If so, you'll should  (un?)format that and let it be unallocated for starters.

Your home partition is inside of the extended partition, so what you should do is expand the extended partiton to eat up that (what should be?) unallocated space.
Then you can extend the home partition to eat the unallocated space.

So basically the space needs to go into the /dev/sde2 partition first before it can be used by the /dev/sde5 partition.

Hope that makes sense.

---

### Post by elliott6 on 2015-09-29
Just helped another user with a similar issue (I believe it's the same).

Refer to this thread - [http://ubuntuforums.org/showthread.php?t=2295968](http://ubuntuforums.org/showthread.php?t=2295968)

It is "tricky," but mainly because it is a little unfamiliar. Just be sure there is enough space after you shrink (I don't see any "unallocated space" from your picture).

You will need to shrink, then move the appropriate partitions, PRIOR to expanding the extended partion. Then the "tricky" part is you need to select the entire extended partition (choose sde2) and expand that before being able to ultimately expand your home partition of sde5. You'll also want to be sure you are doing this when the partitions are not mounted - use a liveCD.

Good luck, and just ask! 

elliott

---

### Post by Ace_Rimmer on 2015-09-29
> **deadflowr said:**
> I'm guessing you created that /dev/sde3 partition and gave it a ext4 filesystem type?
If so, you'll should  (un?)format that and let it be unallocated for starters.

Your home partition is inside of the extended partition, so what you should do is expand the extended partiton to eat up that (what should be?) unallocated space.
Then you can extend the home partition to eat the unallocated space.

So basically the space needs to go into the /dev/sde2 partition first before it can be used by the /dev/sde5 partition.

Hope that makes sense.

Hi, I'm stupid, I put up the wrong picture.  It should have been the one with the unallocated data in the space between the partitions.  It won't let me add the space to any partition other than sde1 and it won't let me expand sde2 at all.

---

### Post by v3.xx on 2015-09-29
I'm getting a fuzzy picture of what’s going on.

Using gparted, turn off the swap partition.  See if that’s the hold up.

---

### Post by yancek on 2015-09-29
You also need to unmount the logical partition (sde5) also before doing anything.

---

### Post by deadflowr on 2015-09-29
> **v3.xx said:**
> I'm getting a fuzzy picture of what’s going on.

Using gparted, turn off the swap partition.  See if that’s the hold up.

> **yancek said:**
> You also need to unmount the logical partition (sde5) also before doing anything.


Both of these apply.
The key symbol means that the partition are mounted and in use.
You need to unmount any partitions that you will be trying to work with.

Best not to try to unmount them on a running system but instead use Ubuntu's installation disk, as it can run a live session; and also contains a functional gparted for just this event.
No partitions will be mounted on a live session, unless you mount them manually.
So all you need to do is pop the installation media in when you start the computer and choose the menu option Try Ubuntu.

depending on hardware, it can take longer to start up versus an installed version.
Once it starts you can search for gparted and start that.

Note v3.xx's advice on turning off swap.
Sometimes the live session might see and try to use any swap partition it can see anywhere it sees it. (as if that makes sense)
You'll need to turn it off if it does.
So highlight the swap partition (if it has a key symbol) and there should be a selection option for swapoff. select it and  swap should be turned off.
But once swap is off and no partitions are mounted then you can move the space into the extended partition which you can then expand into the home partition.

Hope that helps.

---

### Post by deadflowr on 2015-09-29
> **v3.xx said:**
> I'm getting a fuzzy picture of what&#8217;s going on.

Using gparted, turn off the swap partition.  See if that&#8217;s the hold up.

> **yancek said:**
> You also need to unmount the logical partition (sde5) also before doing anything.


Both of these apply.
The key symbol means that the partition are mounted and in use.
You need to unmount any partitions that you will be trying to work with.

Best not to try to unmount them on a running system but instead use Ubuntu's installation disk, as it can run a live session; and also contains a functional gparted for just this event.
No partitions will be mounted on a live session, unless you mount them manually.
So all you need to do is pop the installation media in when you start the computer and choose the menu option Try Ubuntu.

depending on hardware, it can take longer to start up versus an installed version.
Once it starts you can search for gparted and start that.

Note v3.xx's advice on turning off swap.
Sometimes the live session might see and try to use any swap partition it can see anywhere it sees it. (as if that makes sense)
You'll need to turn it off if it does.
So highlight the swap partition (if it has a key symbol) and  a right click with mouse there should be a selection option for swapoff. select it and  swap should be turned off.
But once swap is off and no partitions are mounted then you can move the space into the extended partition which you can then expand into the home partition.

Hope that helps.

---

### Post by Ace_Rimmer on 2015-10-06
I haven't had time to fix this but I'll give these suggestions a try tonight.

---

### Post by Ace_Rimmer on 2015-10-06
Well I turned off swap and it let me grow sde2 to the size of the  unallocated space. Now I'm expanding sde5 into the rest of the space.   Its telling me it may not boot but we will see.  Thanks for the help.   I'm used to running Linux servers and file shares but this was the first  time I really messed with the partitions.  Its doing the move now, hopefully on a fast SSD it won't take that long....

---

