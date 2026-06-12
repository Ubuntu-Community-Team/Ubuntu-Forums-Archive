---
title: "Expand Virtual Drive Size - After Install"
date: 2007-05-12
forum: General Help
---

### Post by goandeatsomestuff on 2007-05-12
Hello,
I've got a quality install of Ubuntu on my machine, and Wubi has worked without a hitch for me thus far (thanks!!!), but my virtual drive is showing only about 4GB of total space, with 1.6 free and 1.4 available.  I had only a bit more than 4GB available on my HDD when I installed Ubuntu, so my question is, will my Virtual Drive's size expand if I free up space on the host drive, or will is remain fixed to the free space I had when I installed with Wubi?
Thanks in advance!

---

### Post by ago on 2007-05-13
It will remain the same, but see the wubiguide for a way to add more space: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by goandeatsomestuff on 2007-05-13
Thanks for the quick reply.  For anyone else, here's the specific text from the wiki:
[quote="[WubiGuide Wiki](https://wiki.ubuntu.com/WubiGuide)"]
How do I resize the virtual disks?

Use Toporesize, available at [WWW] [http://csemler.com/cs.html](http://csemler.com/cs.html) and resize system.virtual.disk (for /) or home.virtual.disk (for /home) or swap.virtual.disk (for swap) in C:\wubi\disks [/quote]

[http://csemler.com/cs.html](http://csemler.com/cs.html) says:
[quote="Chris Semler"]
Download [toporesize (www)](http://csemler.com/toporesize-0.7.zip)
A tcl/tk front end for e2fsprogs. mainly used with Topologilinux and coLinux for creating and resizing ext2 and ext3 filesystem images. This uses the cygwin1.dll and may conflict with other programs compiled under cygwin so you may need to make sure you have no other cygwin based programs running when using toporesize. Toporesize is packed as a Starkit. [/quote]

Toporesize is a Windows program.

---

### Post by jegHegy on 2007-05-14
I tried this yesterday, e2fsck complained that the FS had some features it did not support and that I should get a newer version of e2fsck, so the method in the Wiki didn't exactly work. And then I dabbled around with tfile.exe and messed up my system image and it all went to hell, but that's another story. :)

---

### Post by ago on 2007-05-14
Good old way: 

1. Create the file extra.virtual.disk of the desired size and place it under C:\wubi\disks. 

2. Boot into Ubuntu and run the following code (you can cut and paste it into a terminal): 

sudo mkfs.ext3 /dev/loop4 
sudo mount /dev/loop4 /media/extra
sudo rsync -avx --exclude '/sys/*' --exclude '/proc/*' / /media/extra

Boot into windows and rename extra.virtual.disk to system.virtual.disk. 

To resize home.virtual.disk the procedure is similar to the above but you have to use: sudo rsync -avx /home/ /media/extra

---

### Post by ecology2007 on 2007-05-14
Anyone has success with it ?
[http://csemler.com/toporesize-0.7.zip](http://csemler.com/toporesize-0.7.zip)
It is a gui for ef2resize written in tcl-tk. It smells very good but ef2resize included version (1.35) asks me to use a better version with the wubi.virtual.disks.
Maybe someone has found some more recent binaries. e2fsprogs homepage only has sources.
[http://prdownloads.sourceforge.net/e2fsprogs/e2fsprogs-1.39.tar.gz](http://prdownloads.sourceforge.net/e2fsprogs/e2fsprogs-1.39.tar.gz)

If there is any cygwin expert here, I am trying to compile e2fsprogs.1.39.
I got gettext package installed in cygwin then

./configure --disable-nls (has stated in toporesize doc)
make


compiles all the binaries but fails on resize !!!:confused:

---

### Post by Sushubh on 2007-05-16
anyone got a reliable safe easy solution? :P

---

### Post by blackjackel on 2007-05-17
> **ago said:**
> Good old way: 

1. Create the file extra.virtual.disk of the desired size and place it under C:\wubi\disks. 

2. Boot into Ubuntu and run the following code (you can cut and paste it into a terminal): 

sudo mkfs.ext3 /dev/loop4 
sudo mount /dev/loop4 /media/extra
sudo rsync -avx --exclude '/sys/*' --exclude '/proc/*' / /media/extra

Boot into windows and rename extra.virtual.disk to system.virtual.disk. 

To resize home.virtual.disk the procedure is similar to the above but you have to use: sudo rsync -avx /home/ /media/extra

This method is a problem for me since I have 3.68GB left on the drive and the installation itself is 3.9gb....

UNLESS you mean that you should create extra.virtual.disk of the desired size to ADD to your existing virtual disk, then I could just create a 3gig file and add it to the existing 3.9gb file to create a file of 6.9 gb. That would work.

I tried the previous method of using tfile to resize the file, which didn't work. Strangely though if you resize the file to 700 megabytes then it will allow you to resize it back up to 7000mb... very  strange.

---

### Post by Cloudedbrains on 2007-05-20
Help - I want to resize my virtual disks (have loads space) but this guide etc is way way way to complicated for my brain to handle :(

Is there anyone who could help me do it step by step in SIMPLE terms please ;)

I had to lower the virtual disk sizes to even get it to install but I have it up and running well now - just need to resize them ;)

---

### Post by ahura on 2007-05-28
I have the same problem as blackjackel... and the same doubt! If this new file Adds space to the existing, great, but, if it doesnt, so it will ruin everything up here. So please, anybody, help us... and black, if you discovered a safe way, please, let me know. thanks. im new on the forum, so i dont know how to use it well , send any news to my e-mail felipeahura at gmail.

---

### Post by ecology2007 on 2007-05-29
There is no easier way to expand the sizes at the moment.
You can make a copy of /wubi/disks/system.virtual.disk before doing it and report your results here.

---

### Post by ahura on 2007-05-29
I still need to know if this file i need to create needs to have the complete size i want for the partition (in this case, my system have 3gb, so i would create a 3.5gb, that is the size i want, and what is impossible since i have only less than 2gb free on my host), or if this new file will add size to the partition, so i would need to create a 500mb, so i would get 3.5gb?

---

### Post by alakalaka99 on 2007-06-01
ok, so i made the extra.virtual.disk, but it wont let me rename to system.virtual.disk, any suggestions?Also i cannot edit my File System hard drive, or my new extra.virtual.disk drive. I dont know if this is normal, if it isnt, how can i mose/take stuff from them?

---

### Post by frease on 2010-02-10
Hi all :) I have the same question on how to successfully increase disk space for wubi. Since the thread is old, sorry to bring it up again but I wish to enquire if after so long, is there a good solution? Thanks!

---

