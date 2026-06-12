---
title: "[SOLVED] Increasing size of wubi partition?"
date: 2008-05-01
forum: General Help
---

### Post by rogerdpenguin on 2008-05-01
I reinstalled wubi, and I chose the 30 gig installation. Is it possible to increase the size of that installation, to something like 60 gigs?

---

### Post by ago on 2008-05-01
30GB should be more than enough for a while... If you really need more, you might considering using a dedicated partition.

---

### Post by jaredbuck on 2008-05-02
I agree, 30 gigs is probably more than enough. Any more than that, you might want to consider installing Ubuntu through the regular live cd(s). Then you can set the exact partition size you want. I myself use Ubuntu through Wubi and I have a 15 GB partition for it. Works well enough for me.

---

### Post by lordmorley on 2008-05-15
I would really like to know about increasing the size of the partition after a Wubi install. I am forced to keep vista or xp on my machines, but for very little usage. 

Frankly, I don't know why I would want to change my current setup. Are there greater benefits of a dedicated partition? I did that before (the first time I tried Ubuntu) and it was very inconvenient, due to booting and wireless issues. 

The absolute ease of my most recent experience with Ubuntu really is a tribute to the Wubi project. I use my machine for everything, and was quickly able accommodate all my computing needs in Ubuntu alone. 

All the sugar aside, why would I want to alter my setup if I don't have to? I appreciate everyone's comments (above), but just because we are Ubuntu newbies, doesn't mean we are computing newbies. There is a reason we all invest in large hard drives: we need the space.  

If expanding the size of the partition for a Wubi installation is not possible, then it is a worthy development goal. 

Well that's just my two cents.

---

### Post by ago on 2008-05-15
[https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by jak.plopelor on 2008-05-15
I am sorry, but it seems as if this thread is not solved:

for it gives no answer on how to increase wubi partition.

talking for myself, as know nothing, the reason I used wubi was just because it was easier, and after a couple of weeks of setting up my computer, almost never using windoz I don't really want to reload ubuntu...

please if any one can help me?

I would appreciate it very much, thanx!

---

### Post by ago on 2008-05-16
Follow the instructions in the wubiguide under the section:

How can I get more virtual disk space manually?

---

### Post by nisarg on 2008-11-03
I have Ubuntu running over Wubi with 15GB. 
Personally - I feel its enough for my OS and programs. But obviously, you can't imagine storing all your data on it. I just plugged in another physical disk NTFS partition 'ed under windoze. Ubuntu 7.10 or over should I presume be able to simply detect and automatically mount it under 'media'; if not should straight forward to mount it manually or at boot time from fstab.  
So while both my OS 'es i.e. windoze.. and Ubuntu run from one disk, both the systems can access a common partition for my data. I dont say there's anything ingenious about the solution - it simply should work - your data it always accessible. 
I think - that should also help performance... atleast in instances like me, where I can SSH from anywhere and listen to my music, or can be running torrents!

---

### Post by nisarg on 2008-11-03
I have Ubuntu running over Wubi with 15GB. 
Personally - I feel its enough for my OS and programs. But obviously, you can't imagine storing all your data on it. I just plugged in another physical disk NTFS partition 'ed under windoze. Ubuntu 7.10 or over should I presume be able to simply detect and automatically mount it under 'media'; if not should straight forward to mount it manually or at boot time from fstab.  
So while both my OS 'es i.e. windoze.. and Ubuntu run from one disk, both the systems can access a common partition for my data. I dont say there's anything ingenious about the solution - it simply should work your data it always accessible. 
I think - that should also help performance... atleast in instances like me, where I can SSH from anywhere and listen to my music, or can be running torrents!

---

### Post by sextheorist on 2010-02-21
From [wubiHelpSite]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")
"You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) 
As an alternative, you can use the following script to move /home to a dedicated virtual disk.   
Download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), open a terminal and run: 

sudo sh wubi-add-virtual-disk /home 15000Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.  
You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab."


but for me it was not that easy.......   :(:(:(
first download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), and then move it your home directory...

then open terminal and type
```
sudo mv wubi-add-virtual-disk /bin
```Give password when asked

then i had to change file permissions of wubi-add-virtual-disk so typed this

```
cd /bin
```then

```
chmod 755 wubi-add-virtual-disk
```then type

```
sudo sh wubi-add-virtual-disk /home 15000
``` where 15000 is size of 
disk in mbs...
:D:D

---

### Post by 3rdalbum on 2010-02-21
Wubi is not really intended for this sort of thing.

Wubi is designed so that new users can evaluate an installed Ubuntu running directly on their hardware, without having to go to the trouble of irreversable partitioning. Once evaluated, it's easy to delete and then make a real dual-boot setup.

Your "booting and wireless issues" should not be present in a regular Ubuntu dual-boot, because even the Wubi installation is running directly on your hardware.

The above poster seems like they can help you with getting a bigger Wubi image, but Ubuntu is still best installed on its own partition for a number of technical reasons, and Wubi is designed to reflect that.

---

### Post by dananimal on 2010-11-17
Why is this marked SOLVED???

There is no solution here.

People deciding that the question is invalid; 'X should be enough space' is not answering the question.

Referencing a section which is no longer on the wubi guide is not a solution.

The re-paste on how to transfer a wubi install to another partition is not a solution.

I have hated the effects of post-count ranks on forums for years and it seems that these forums are suffering the effects of 'how many "cups" of ubuntu' people's handles have.

Topics should not be marked SOLVED until they have a solution.

---

### Post by Chaaaaaaaalie on 2010-11-17
[SIZE=3]Actually, I followed [COLOR=#000000]sextheorist's instructions on page 1, and it worked, so it seems solved to me.[/COLOR][/SIZE]

---

### Post by jwbrase on 2010-11-17
I agree, the OP's question doesn't seem to have been answered. (Unless he himself decided that using a dedicated partition was the way to go and marked it solved himself). OTOH, if you start running out of room on your virtual partition, it probably *is* better to switch to a dedicated partition, seeing as Wubi's virtual partition can be fairly fragile in the face of things like hard shutdowns.

That said: This thread has been necromanced twice and is over two years old.

---

### Post by echo6 on 2011-02-25
I would consider myself a reasonably experienced Linux user, I would have to agree that this thread is not solved.

I'm using wubi because I wanted to do something quickly in Linux, but now I also want to increase the ridiculous partition limit of 30Gb!

With 500Gb disks being so cheap, 30Gb seems extremely stingy!

Yeah! I have dedicated Linux boxes, but for on this occasion I need the native Windows OS to remain, and also have the option to boot to Ubuntu without having to go through the pain of NTFS resize and partition release to install Ubuntu.

---

### Post by bobc4012 on 2011-02-28
I agree echo6. Also, while Sextheorist's solution works if your Wubi install creates a single virtual disk (root), I have not been successful with it as my Wubi install creates 3 virtual disks (besides swap) - root - home and usr. My usr directory/virtual disk filled up, which left me in a bind. LPVM will create a root virtual disk (and transfer the files), but it will not create a home nor a usr virtual disk in later releases. I think the last time I was able to use LPVM to do what I need was in 8.10 or earlier, I don't recall. I am currently trying to figure a way to move my /usr directory into a new "usr.disk". Explor2fs doesn't work properly anymore (I believe it is due to the .disk files now being EXT4). Ext2IFS will read these .disk files, but not write - otherwise, I could delete the "new.disk" and copy the usr.disk or the home.disk contents to the "new.disk". It would be nice if Wubi would provide some additional configuration parameters - also if partition editor would handle virtual disks. It appears the alternative is to stay on an earlier version of Ubuntu that uses EXT2/EXT3 partitions. 

I understand there are "linux purists" who would never use Wubi (but I'll bet they use virtbox or vmware). However, some of us have good reason to use a Wubi install. It would be "nice" if they answered the specific question rather than going off on a tangent. I see this happen too often on these forums. All it accomplishes is turning off the person who asked the question and send them back to Windows. 

I have done dual booting and have had more problems and re-installs with dual booting than I have had with a Wubi install. As far as performance, I notice very little performance degradation.

---

### Post by bcbc on 2012-02-01
This is an old thread - but it's still being referenced. This is a warning not to use LVPM on Wubi installs anymore. LVPM hasn't been updated since release 8.04 and it lists grub-legacy as a dependency so it will uninstall grub2 (package grub-pc).

The main result of this is that your grub.cfg will no longer be updated (new kernels will not show up).

Please instead refer to the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F") on how to resize the root.disk.

---

### Post by Zgamer01 on 2012-04-09
Thanks so much!

---

