---
title: "Resizing partitons without formatting"
date: 2007-02-27
forum: General Help
---

### Post by Moses on 2007-02-27
I have a 120Gb disk, 5Gb for Ubuntu and 500Mb for swap space, the rest ntfs with XP.

I have grown attached to ubuntu and want to start using as my main OS, I don't mind leaving all my media on my ntfs partition, but I still need some more space for the ext3 partition. 

Is it possible to safely "transfer" another 5gb from ntfs to the ext3 partition, **without** formatting, or reinstalling anything? 

I've read a few horror stories so I want to go about this carefully. I have Partition Magic 8 in XP, and I could easily make the resize there, but something tells me it's not a good idea. Is it better to do it from the Linux side? Or perhaps from a LiveCD? 

How failsafe would this operation be? Basically what is the worst case scenario? I really can't afford to lose any time/data.

Could someone post some good advice, and then if enough people give it a vote of confidence I might be brave enough to try :-D . On the other hand, if someone posts some shaky information please veto it :)

---

### Post by milton1 on 2007-02-27
Live cd is probably your best option. If PM has no such utility, you can use gparted live. I have had good success with it.

---

### Post by clint1010 on 2007-02-27
I have found gparted to be very reliable and easy to use. I have had success before resizing an ntfs partition with it from linux.

I wouldn't try resizing a partition with windows.

Always backup your data before doing anything to a partition, but that goes without saying.

---

### Post by Moses on 2007-02-27
So booting with a LiveCd and then resizing the partitions with gparted is a good idea? 

Is it not possible to break the ntfs or ext3 structure? I've certainly read stories about this happening... :confused: 

As long as it's 95% safe, and there is an emergency recovery option I can perform, to at least recover my data, I'm happy.

I'll let this thread go own for a few more hours, before I make my decision.

Thanks!

---

### Post by clint1010 on 2007-02-27
by judging your concerns, I guess you have some very important data on that ntfs partition, definatly backup your data.

---

### Post by rsambuca on 2007-02-27
I would definitely use the gParted live CD instead of the ubuntu live CD.  The gParted CD is more up-to-date than the ubuntu CD.  Also, your quote here really scares me> As long as it's 95% safe, and there is an emergency recovery option I can perform, to at least recover my data, I'm happy..  Yes, it is probably not going to be a problem, but please backup your data FIRST.

---

### Post by Moses on 2007-02-27
hehe.  Nothing too serious.

Even if I do backup, it is still a huge hassle if something goes wrong. 

I had little fear when I created my ext3 partition a few days ago by allocating some free space with PM8 in XP. I'm just not totally comfortable in this environment yet.

---

### Post by clint1010 on 2007-02-27
I would consider it to be very small risk. I know a few ubuntu users, and linux users in general that have performed this operation without a hitch.

---

### Post by Moses on 2007-02-27
Okay, I'm going to go ahead with it now. I only have 2mb free on ext3.

Thanks everyone.

---

### Post by Moses on 2007-02-27
:-s So I booted livecd, ran GNOME partition manager and then shrunk my ntfs by 5gb. I then applied this operation, and everything works perfectly. :)

Now when I run livecd again, it won't let me grow the ext3 into this space :-s . (it lets me grow the ntfs, though).

If I boot into XP and run PMagic8, it **does** let me grow the ext3 to fill the 5gb unallocated space.

How do I get gparted to allow this operation? Do I have to first format the unallocated space to ext3? (that doesn't make sense to me)

---

### Post by rsambuca on 2007-02-27
I assume you are trying to add to the front of the ext3 partition?  The gParted live CD will allow you to do so.

---

### Post by Moses on 2007-02-27
You are correct. I have since fixed the problem by moving the ext3 partition to the 'left' with PMagic, and then using gparted to add the free space to the 'right'

Thanks everyone for the help.

---

### Post by jdackle on 2007-02-28
Glad that Moses got to do his thing! \\:D/ 


Now about my question!! :mrgreen: 

This is my current hd layout (taken from GParted):

hda1 - 19.53Gb - ntfs
hda2 - 17.73Gb - Extended
   hda5 - 17.73Gb - ext3
n/a - 7.84Mb - Not allocated

I'm thinking to do the following:
1. Shrink the hda1 partition by some 256Mb.
2. Move the hda2 (purposedly so that it moves the hda5 within) back to just after the new hda1 will end.
3. Create a new swap partition (as of now I have none) at the end of the disk, i.e. after the hda2/hda5 one.
OR
3. Enlarge the hda2(but NOT hda5 to the end of the disk and THEN create a new sap partition "inside" the LBA hda2 partition.

I'm pretty sure there will be no problems with step 1.
Regarding step 2, I think it will work that way, but am not sure. :confused: 
On step 3, I'd really apreciate your thoughts...:confused: 

Thanks in advance!

---

