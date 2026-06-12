---
title: "dual boot help and ?'s"
date: 2008-05-02
forum: General Help
---

### Post by creekchub on 2008-05-02
i am in the process of making a dual boot rig. i am going to be using ubuntu.  anyhow i was told i need to install windows first.  which i am attempting to do.  my new rig is an msi K9N6SGM-v with a athelon 64 2.4 ghz single core processor and 2 gigs or DDR2 800.  when i get to the partition the hard drive it only recognizes 76,000 mb.  is this a problem? i have an 80 gig hd.  also what kinds of partitions should i use for optimum performance.  help is appreciated.

---

### Post by Bakon Jarser on 2008-05-02
The hard drive size has to do with the way hard drive manufacturers report hard drive sizes compared to the way OS's read that size.  There have actually been a couple of lawsuits about it.  So this is normal and nothing to worry about.  I personally have a 15GB windows partition, 10GB home partition, 10GB root partition, and the rest is an NTFS storage partition.  This works well for me, other people might think my home or root partition are a little small.  It's my personal preference.

---

### Post by Bakon Jarser on 2008-05-02
Forgot to mention you'll need a swap partition too.  Mine is 2GB.  I think you're supposed to base it on how much RAM you have.  Something like RAMx2 but don't take my word for it on that.

---

### Post by creekchub on 2008-05-02
so is 76,000 my whole hard drive?  which does not make sense to me if so what #'s do you use to brake it down.  or should i just install windows on the whole thing and then repartition when i install ubuntu?

---

### Post by zaussome on 2008-05-02
z

---

### Post by creekchub on 2008-05-02
so should i install windows on this single partition and then repartition when i install ubuntu?  or do i need to brake it down before i install the windows?

---

### Post by Bakon Jarser on 2008-05-02
you've got options.  if you want the easy solution install windows using the whole drive and then install linux and let it repartition your hard drive.  if you've never installed linux before then I would recommend this option.

Another option is to install windows using the whole drive and then use wubi to install linux inside of the windows partition, no partitioning necessary.

You're other option is to install windows on whatever size partition you choose and then when installing linux choose manual partitioning when the option presents itself and make a swap partition and a root partition to install on.  This is a little more of an advanced option, not too difficult but definitely more complicated then the first two.

i wouldn't worry about seperating the home partition from the root partition.  it's very nice to have if you ever have to reinstall linux because all your configuration files for your programs will still be there but it's not exactly efficient use of space.  

good luck.  if you have any more questions i'll monitor this thread for a little while.

---

### Post by creekchub on 2008-05-02
thanks for the information,i am all about easy but functional. even tough i have built and install my last 4 pc's i still feel that i am just a beginner.  i want to get away from windows eventually but not ready for the total move yet.  i guess what i want to know is if i install windows on the whole drive and repartion with linux can i make a swap partition and a fat 32 partition ect. ect ect?

---

### Post by Bakon Jarser on 2008-05-02
> **creekchub said:**
> thanks for the information,i am all about easy but functional. even tough i have built and install my last 4 pc's i still feel that i am just a beginner.  i want to get away from windows eventually but not ready for the total move yet.  i guess what i want to know is if i install windows on the whole drive and repartion with linux can i make a swap partition and a fat 32 partition ect. ect ect?

yes, the linux installer comes with a partitioner.  but fat32 is dead, windows doesn't use it and neither does linux.  linux uses ext3 and windows uses ntfs.  it sounds like the solution that you're looking for is to install windows on the whole drive and then run the installer on the linux disk.  let it do the automatic partitioning.  i haven't actually used that before but I believe it will ask you what percentage of the disk you want to use.  it will set up a swap partition and everything automatically for you.

---

### Post by creekchub on 2008-05-03
thanks everyone for all your help.  i got up this morning and formatted the partition and installed windows.  popped in the live  ubuntu cd and i am currently running it and typing this while using it.  i will give some tests today to make sure it will operate ok on this new rig.  here are the specs.

MSI K9N6SGM-V, amd athelon 64 single core 2.2 ghz processor.  2 mb of ddr2 800 ram. nvidia 6100 onboard video

---

