---
title: "Ran out of /home space"
date: 2012-10-25
forum: General Help
---

### Post by iiVoxel on 2012-10-25
How do I give more memory to /home with gparted? I created a seperate partition thinking I could install stuff to it, but for some reason I can't figure out how. So, how can I merge the partition labeled "Space" with the one mounted at /home. Oh yeah, and merge the "unallocated" ones too.

---

### Post by LiamOS on 2012-10-25
Assuming there's nothing of value there, you could delete that 'space' partition and move the rest up, then expand the /home into the space. You can only really expand a partition into space next to it.
[B]Also, make sure to back everything up.
[/B]
Edit: You'll have to do this from a live CD, since the partitions have to be unmounted. If you have your ubuntu installation disk around, that probably has gparted on it, from which you can do it.

---

### Post by newb85 on 2012-10-25
That's not really a "space partition"--it's just unallocated space, so there's nothing to delete.  Since that space is directly after you /home partition, it should be relatively easy.

[LIST=1]
[*]Boot into a Live session (CD, DVD or USB) of Ubuntu.
[*]Open Gparted.  Right-click the /home partition and click Resize/Move.
[*]Add the amount shown in "Free space following" to the "New size" amount.  This should set "Free space following" to zero.
[*]Click "Resize/Move".
[/LIST]

---

### Post by iiVoxel on 2012-10-25
Thanks! But one more question cause I'm a Ubuntu newbie >_< How do you boot into a Live CD? I do have the installation disc still (always will in case I ever need it) and when I put it in it loads up what language to go through install first, where do I choose Live CD? Thanks!

---

### Post by lisati on 2012-10-25
> **iiVoxel said:**
> Thanks! But one more question cause I'm a Ubuntu newbie >_< How do you boot into a Live CD? I do have the installation disc still (always will in case I ever need it) and when I put it in it loads up what language to go through install first, where do I choose Live CD? Thanks!

When you boot from the CD, there should be an option "Try Ubuntu without installing"

---

### Post by iiVoxel on 2012-10-25
> **lisati said:**
> When you boot from the CD, there should be an option "Try Ubuntu without installing"


This ( [http://www.youtube.com/watch?v=otFepT3IhAw](http://www.youtube.com/watch?v=otFepT3IhAw) ) is what I get. Am I just missing it??

---

### Post by newb85 on 2012-10-25
That does not appear to be a standard LiveCD.

---

### Post by iiVoxel on 2012-10-25
I downloaded the iso of the one posted here ( [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) ) named "Ubuntu 12.04 LTS". Burned that to a disc. Put in my computer and followed the instructions (I choose "Install Ubuntu") Should I do the same with Ubuntu 12.10 because maybe the LTS has a weird boot install?

---

### Post by oldfred on 2012-10-26
You do not want Install as that will install another copy of Ubuntu. 

You want the try Ubuntu.

---

### Post by iiVoxel on 2012-10-26
There is no screen like that, it shows like in the link I posted.

---

### Post by newb85 on 2012-10-26
Could hardware limitations be preventing the normal Ubiquity screens and Live session availability?

Perhaps more details on your system hardware would be helpful.

---

### Post by iiVoxel on 2012-10-26
I fixed it! I just did a full reinstall formatted all the disks and what not and managed the partitions better. I still don't know why I get that look of install but `\0_0/` oh well. I also thought It may be my computer hardware capablities but I can run Minecraft @120Fps and also all the cods on low setting @50Fps, so I don't that SHOULD be the case.

---

