---
title: "xfs partition table on RAID array"
date: 2015-11-13
forum: General Help
---

### Post by p4cm4n88 on 2015-11-13
Hi.

So, I'm usually fairly knowledgeable, and with google on my side am able to figure things out. This time however, I'm at a loss for figuring out what to do.

background : 
I have a server I built, using ubuntu 14.04LTS, with a highpoint rocketraid 2720sgl sas raid card, attached to 8x1TB drives, setup as a RAID 5.
Ubuntu is serving up this raid array with my media on it, using plex, and many other applications depending on what i need. the raid array is OLD. it was initially setup in 2007, as a 4x1TB, then grown and grown and grown. earlier this year, a drive died. i then opted to replace it using new western digital drives (blue...stupidly, they were on sale).
upon growing, the array failed. i tried just about everything...finally just went out, bought 2x4TB, copied EVERYTHING over, and rebuilt the array from scratch, and moved the files back.

the array now is one massive 6.5TB partition using XFS. 

if I go to move massive amounts of data at once, a drive fails. its one of the new blue drives, it varies which one. I don't think they wanted me to use blue drives...but oh well, they were 30$. save for massive file movement - this setup has worked flawlessly for about 6 months. i've had to rebuild twice.

now to the issue :

the other day, upon an issue that happened (the server is headless, i didn't have a monitor attached, and stupidly when it wasn't responding, i just power cycled it.) after reboot, nothing came up. i plugged in a monitor, and it started showing that my massive partition couldn't be mounted (its noted in fstab by UUID)...so i booted, and noticed that in the left side, on the launcher bar, it showed 5 random drives (random sizes, a 2.8GB, a 17GB, etc...nothing near any one drive in capacity) ....upon some searching on the system, i realized that for some reason, when the array failed and started rebuilding, the partition table was erased (i guess) and somehow its now reading an individual drives partition table (the raid card shows all 8 drives, now after rebuild, in normal functional operation...however partition table still doesn't show) 

i can manually mount the partition, and it acts as if nothing is the matter...except on reboot, it still tries to mount the other 5 partitions and won't mount the only partition that actually exists - which is supposed to be the entire drive, all 100% of the drive. in parted, the only thing listed is 1 partition, xfs, all 7001GB. the table is listed as loop (not GPT, as it was). blkid shows the other random partitions - does not show my 7001GB partition.

i've researched and researched, and most places tell me to use a tool called testdisk. this is supposed to find your partitions, and recreate your partition table....the problem is, as always with this raid array...with massive IO, the array fails or the system locks...so when testdisk tries to read all 800,000 units, it gets a few thousand in and freezes. a few other tools, gpart among others do the exact same thing.

now, i know when i've grown the xfs partition in the past, i could just delete the partition and recreate it. could i do the same thing in this instance, but with the partition table? would it erase the data? last i knew, the partition was quite literally the whole drive. 

its possible i screwed something up during the array rebuild and it didn't completely rebuild the partition table (if thats even possible). but at this point, i don't know what to do. i could just live with it, and mount /dev/sdc every launch....or who knows.

any and all help is appreciated. i can do whatever commands, and can list the output.

---

