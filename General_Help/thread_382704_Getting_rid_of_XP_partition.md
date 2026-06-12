---
title: "Getting rid of XP partition"
date: 2007-03-12
forum: General Help
---

### Post by Doug11 on 2007-03-12
I am dual booting Ubuntu and XP. I want to go with Ubuntu as my primary and get rid of XP. Is there a way I can get rid of the XP partition and have my whole HD for Ubuntu without having to reformat. It took a while to get it to where I like it, would be a shame if I had to reformat and do it all over again.

---

### Post by buuntuu! on 2007-03-12
not sure, if i'm right here, but if you've got a separate /home partition, won't a clean install (providing you manually edit your partition table) leave it unaffected?? just a thought.

---

### Post by gh0st on 2007-03-12
> **Doug11 said:**
> I am dual booting Ubuntu and XP. I want to go with Ubuntu as my primary and get rid of XP. Is there a way I can get rid of the XP partition and have my whole HD for Ubuntu without having to reformat. It took a while to get it to where I like it, would be a shame if I had to reformat and do it all over again.

I take it you want to resize your Ubuntu partition to take the space from the XP partiton. You could use Gparted to do it nice and easily. The Live CD is great, just download the ISO burn it, boot and you have complete control over your disks.

Check out the Gparted Live CD - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

If you want to back up your current setup you could make a system image with PartImage. It's not that straight forward but it lets you make a decent image like Norton Ghost. There are plenty of good guides around for it as well.

[http://www.partimage.org/](http://www.partimage.org/)

Hope that helps a bit. I got rid of my XP partition and reclaimed the space a few months back and it feels great :) 

Good luck.

EDIT: forgot to say if you need anything, let me know.

---

### Post by laidback on 2007-03-12
You can do this with Gparted. See System>Administration>Gnome partition editor. Have a look but don't action anything right now. You cannot adjust mounted hdd's. Note the greyed out Resize/Move options. On the live Ubuntu cd is Gparted. If you run that you will be able to unmount your hdd (hda1 I should think) then delete the Windows partition and resize/move the Ubuntu partition.
If you don't have the Live cd look here

Live Gparted cd download
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
and documentation for Gparted
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by khedron on 2007-03-12
I think GParted has a way of resizing partitions. You would have to boot the Live CD and open up GParted from there, then resize your Ubuntu partition.

You'll have to look some of this up; I did all this a fairly long time ago.

Edit: damn you fast typers

---

### Post by gh0st on 2007-03-12
> **khedron said:**
> Edit: damn you fast typers

lol :) :)

---

### Post by Doug11 on 2007-03-12
> **laidback said:**
> You can do this with Gparted. See System>Administration>Gnome partition editor. Have a look but don't action anything right now. You cannot adjust mounted hdd's. Note the greyed out Resize/Move options. On the live Ubuntu cd is Gparted. If you run that you will be able to unmount your hdd (hda1 I should think) then delete the Windows partition and resize/move the Ubuntu partition.
If you don't have the Live cd look here

Live Gparted cd download
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
and documentation for Gparted
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

These seem to be all i386,, I have amd64,,will it the Live cd still work? Or should I use one of the Platform Independent ISO's?

---

### Post by gh0st on 2007-03-12
I think you can use the normal Live CD, I have an AMD64 machine and I just downloaded the normal i386 ISO. It booted fine for me and let me re-partition my disk.

I think you should be fine :)

---

### Post by dwasifar on 2007-03-12
+1 on using the live CD.  You might consider NOT resizing your main partition into the empty space though.  Why don't you format it as a separate partition and use it as a storage partition, or as your home partition, if you don't have one set up already?

Gparted is one of those things that really makes you appreciate free open source software.  Every time I use it, I'm reminded of what partition size management options are available natively in Windows (none - inexcusable!), and how much Partition Magic costs for Windows (a lot).  I had gotten used to that situation, so when I first started playing with Linux I was amazed that a full-featured partition editor was built right into the distro.  And it still makes me smile whenever I fire it up.

---

### Post by Doug11 on 2007-03-12
> **dwasifar said:**
> +1 on using the live CD.  You might consider NOT resizing your main partition into the empty space though.  Why don't you format it as a separate partition and use it as a storage partition, or as your home partition, if you don't have one set up already?

Gparted is one of those things that really makes you appreciate free open source software.  Every time I use it, I'm reminded of what partition size management options are available natively in Windows (none - inexcusable!), and how much Partition Magic costs for Windows (a lot).  I had gotten used to that situation, so when I first started playing with Linux I was amazed that a full-featured partition editor was built right into the distro.  And it still makes me smile whenever I fire it up.

I installed Gparted and ran it. It picks up all my partitions but when I click on my Xp partition, it won't give me any options to be able to do anything with it. But now when I go to open it up again, I'm noticing that it was Gnome Partition Editor that I tried, not Gparted, or are they the same. I looked around but did not see anything similiar to 
Gparted anywhere. Does it install to a certain directory or somewhere?

---

### Post by Doug11 on 2007-03-12
OK, i just ran it in the terminal and got it running, but it does the same thing, here is a shot of what is looks like, I highlight the partition I want to delete and format for storage like you say, but everything is greyed out. Am I doing something wrong here?

---

### Post by laidback on 2007-03-12
Gnome Partition Editor is Gparted.

---

### Post by laidback on 2007-03-12
Looks to me as though you might be trying to change the mounted partition /dev/hda, you cannot alter a mounted partition.
Are there any other partitions availabe?, use drop down top right to view choices.

---

### Post by buuntuu! on 2007-03-13
hello again doug11
laidback is right, your partitions are mounted (active) to be able to do anything to them, right-click-em and select "unmount".
but as you are trying to mov/resize your linux-partition as well you have to unmount it as well, which obviously is not possible while you are running your system. (like changing a wheel of your bike while riding it) so there is no alternative to running a live-cd (eiterh your install cd or  the gparted cd.
however, learn about what you are doing BEFORE doing it, again i recommend [psychocats page]("http://www.psychocats.net/ubuntu/"), it's quite a short read but it gives you the basics

---

### Post by Doug11 on 2007-03-13
Thanks, I'll look into that and take my time. It's only 10 gigs I'll be saving, but with a 60 gig drive,,it makes a lot of difference in space.

---

### Post by gh0st on 2007-03-13
I had problems using Gparted from within Ubuntu myself, I found that the easiest thing to do was burn off a copy of the Live CD and boot up from that. It runs from RAM disks and therefor you have full control of you HDD and all the partitions.

I know other people use Gparted from within Ubuntu and that's cool, I just found the Live Cd was by far the easiest and best solution for me. You should really try it, no need to worry about unmounting partitions or anything.

Just a suggestion, do whatever works for you :)

---

### Post by Pugwash on 2007-03-13
> **Doug11 said:**
> I am dual booting Ubuntu and XP. I want to go with Ubuntu as my primary and get rid of XP. Is there a way I can get rid of the XP partition and have my whole HD for Ubuntu without having to reformat. It took a while to get it to where I like it, would be a shame if I had to reformat and do it all over again.

I was in the same position. This is how I did it roughly:

1.) Backed up ubuntu system using this method - [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)   . Copied the backup file onto an external hd.
2.) Installed ubuntu again choosing the option to wipe my Hard disk.
3.) After install made a copy of the "/boot "folder on to the external hd.
4.) Restored previous system, as mentioned in the link.
5.) Copied back the "/boot" folder, overwriting the old one. 
6.) Restarted.
(I recommend restarting a second time before settling in, grub doesn't seem to  immediately notice any newer kernels from you previous system) 

Hope that helps. I had some problems because I didn't do step 3 and 4 the first time, so grub was pointing to a non-existent partition - [http://www.ubuntuforums.org/showthread.php?t=362155](http://www.ubuntuforums.org/showthread.php?t=362155) .

---

### Post by Doug11 on 2007-03-13
So I should be able to just run a Live cd to the point where Gparted starts, delete and reformat the old XP partition and I then should be able to use it as, let's say, a media storage partition????

---

### Post by gh0st on 2007-03-13
Yeah I think so. I don't know if you can use Gparted on the Ubuntu Live CD for this but you can definitely do it with the Gparted Live CD, its only small to download and burn. Boot the CD, reformat the partition to ext3 and then boot into Ubuntu again. I've done it. Worked for me and I'm no genius :) ;)

---

### Post by Doug11 on 2007-03-13
Great, thanks. Will give it a whirl. Everything should work ok as long as I dont touch my main ext3 partition.

---

### Post by konungursvia on 2007-03-13
Gparted is the one you tried, but make sure you have a recent edition. I recommend creating a Fat32 partition and saving any photos or essentials you want to keep from windows on them, then delete your xp partition, then grow your others to fill its empty space. Bye bye M$

---

### Post by laidback on 2007-03-14
The Live CD version of Gparted I have s version 0.3.3. The default Ubuntu version is 0.1.
I think konungursvia is right, it's a good idea to use the latest version.

---

### Post by gh0st on 2007-03-14
Yeah I'd agree with that as well, I used Gparted 3.2 Live CD when I did my machine but that was the latest version at the time. 3.3 is the current version, don't know what changes have been made but it's usually a good idea to go for the most recent stable version.

Good luck :)

---

