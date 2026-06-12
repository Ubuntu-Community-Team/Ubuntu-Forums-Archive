---
title: "Help: Can't read my ext3 partition"
date: 2008-03-09
forum: General Help
---

### Post by MrZehl on 2008-03-09
Aaarrgh. Something went terribly wrong.

 I booted PCLinuxOS and got the message that my sda7 partitiiopn had to be checked. PCLinuxOS stopped the booting process and put me to the commandline. So I booted in Unbunt again. Damn PCLinux OS. Switching between Ubuntu and PCLinuxOS already gave me problems with my partitions but that was fixable with fsck. 
 
The partition seemed missing. I fsck' it it and got a lot of errors. In Gparted I see the partition but the superblock can't be read.
Testdisk sees the 500Gb disk as 385Mb disk. That's the size of the first partion of that disk. It's just a boot partition. 

So my big partition with ext3 is missing. How can I recover my data? Please let someone have a good idea. It's the wordt possible partition to crash. I really need the stuff on there. 
I know I should have backupped it, but I didn't. Stupid me.

Can I rebuild a superblock? Is there some recovery software to fix the partition or that reads the data and writes it to a new disk?

---

### Post by justsomedude on 2008-03-09
So, you already did a manual fsck?

Then I'd give ddrescue a try, it's available in Universe. Never tried it myself though...

Good luck.

---

### Post by MrZehl on 2008-03-10
Hmmm.. strange.... really really strange... Suddenly everything is ok.

I also tried System rescue disk. Didn't want to boot properly either. Maybe the cd was misburned. I don't know. Anyway.... I booted in Ubuntu. I installed gddrescue. Read the documentation and saw you had to really now wich blocks you want to copy and so. Well... it was late, so I started my Deluge Bittorrent Client and went to bed. 

Tomorrow we'll see a new new episode of 'Indiana Jones and the Lost Partition'... I thought.
 
And now.... it seems everthing is al right. Is cab see the partition and the files and folders. It seems complete. I don't know or every tiny bit of  the 480 Gb for files and folders is okay, but it looks right.

For now, I think I'll get me a new external harddrive to backup everything. :)
 
I am happy, but very curious... what happened? Does Ubuntu automaticly start maintenance programs to solve this kind of problems? I'm really surprised.

Anybody can explain this mystery?

---

### Post by MrZehl on 2008-03-11
Ouch... it was not as wonderful as I thought.

While backing up the partition to a external drive, the partition suddenly wasn't readable anymore. So I backed up half of my data. So still half is missing. fsck.ext3 can't recover it.
In nautilus I don't see the partition anymore. With the partition editor I still can see the partition and the amopunt of data on it. 

The Ubuntu Livecd won't boot, because it of drive errors. Really a lot. Is there some program that I can use to recover my data. Prefferably free of course, but the most important thing is to recover my data. So if the best option is a commercial program, it'll do.

Please... can anybody help me? 
I installed gddrescue, but I don't know how to use it. I don't know the right parameters to use.

---

### Post by MrZehl on 2008-03-12
Okay... I did try gddrescue to copy alle data from the broken partition to my new external drive without start and end parameters.. On the destination drive was already half of the tha data. When I started gddrescue, all that data was disapeared. .... Aaargh..

gddreascue is still busy and will be for a couple of days with the current speed. On my destianation drive is although only a unrecognised file, wich should be a directory containing all data. I hope this is temporary whlie the process is running and after gddrescue finished the direcory will be recognised as directory and the recovered files will be readable.

But I have to wait for a couple of days till the process finished. If it's not fixed at the and of the prcess gddrescue will have deleted my already recovered data instead of recovered the missing data. I cross my fingers.

---

### Post by Zorael on 2008-03-12
I believe **testdisk**, which is in the official repositories but you may need to enable the universe ones in Software Sources, can also help you with recovering partitions.

I've only had my partition table deleted, so I don't know the details myself.

---

### Post by Fire_Chief on 2008-03-12
Sounds like your drive is dying. It's sometimes working and sometimes not. You *could* try an old techie trick (that has **no technical merit** mind you but has sometimes worked when all else failed) by putting the drive in a ziplok bag and stick it in the freezer for a few hours. Then pull it out and immediately try to read data off before it gets to room temp again.

Regardless, the drive will probably need to be replaced very soon.

Good luck!

---

