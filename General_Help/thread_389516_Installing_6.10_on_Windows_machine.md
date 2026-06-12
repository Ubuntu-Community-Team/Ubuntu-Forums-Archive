---
title: "Installing 6.10 on Windows machine"
date: 2007-03-20
forum: General Help
---

### Post by FlyingIsFun1217 on 2007-03-20
Hey,

I've tried out the live cd of 6.10, and I have to say that I would love to be able to use it as my primary OS (not to mention being able to port my software to linux), so I figured I would install it.

Well, some strange things. And me being strange :)

HP set up my computer so that there are 2 partitions on the primary hard drive. That kinda messes around with me.

Here's what I want to do though: Dual boot Ubuntu 6.10 and Windows XP.

When I use the installer on the live cd (which was ordered through the site, very nice how you can do that :)), it gives me the option of 1. Wiping the whole hard drive 2. Use the most free space, and 3. Manually partition the HD.

How do I go through this without messing up the Windows stuff?

Thanks for helping a newbie :)
FlyingIsFun1217

---

### Post by twikletoes on 2007-03-20
How big is each partition?
If one takes up most of the drive and the other takes up very little (i.e. 8MB) then that is how windows installs automatically. the only way to stop windows from doing that is to make a partition of the size you want (maybe half or so) then install it on that.

You will want to somehow save your files, maybe to another computer if you have one, then reinstall windows the way i said.
Then you can install Ubuntu to the open partition.:)

---

### Post by FlyingIsFun1217 on 2007-03-21
Well, I would love to, but thats how it was automatically setup. I bought it preconfigured with windows, and as almost all new computers, it came with no windows install cd.

Can I just partition it off using the Ubuntu installer? And if I do, what should I select for the rest of the install (Where to put root / directory and what not)?

Thanks again!
FlyingIsFun1217

---

### Post by mrmonday on 2007-03-21
> How big is each partition?

Could you tell us this? You need to make sure not to damage the one windows is not on... This will be your restore partition, instead of a windows CD. You will need to keep this in tact in case anything goes wrong.

If you are manually editing the drive, you need to shrink the main windows partition, then install Ubuntu in the space.

---

### Post by FlyingIsFun1217 on 2007-03-21
It seems I have found some crude directions at [http://news.softpedia.com/news/Dual-Boot-Ubuntu-and-Windows-47701.shtml](http://news.softpedia.com/news/Dual-Boot-Ubuntu-and-Windows-47701.shtml) about how to partition the drive right to install ubuntu without disturbing windows. Here's what it says:

1) Defragment Windows
2) Use installer, when at partitioning screen, select 'resize IDE1 master and use free space'
3) Tell it how much space is to be used for the linux partiton
4) Install, reboot, and everything is good through GRUB

This will work, right?

Thanks a million!
FlyingIsFun1217

---

### Post by mrmonday on 2007-03-21
When you are at the partitioning screen it will show your two partitions. You need to resize the main windows one (most likely the bigger one - you can check the size in windows to make sure). Other than that everying seems right.

---

### Post by tcrroadie on 2007-03-21
Like mrmonday said, the smaller partition contains your backup image of Windows.  Hence the reason you do not have a Windows installation cd.  

The safest solution that I would recommend for you, is to purchase an additional hard drive (they are cheap as dirt these days) to install as a slave hard drive in your system.  Keep your original OEM hard drive as is and install Ubuntu on your new slave hard drive.  This will allow you to easily duel boot between your original Windows installation and Ubuntu without fear of borking your original Windows installation and the backup partition on your master hard drive. 

Using 2 hard drives in your pc will look something like this. 

Hard drive one. (Master, containing backup Windows partition and main Windows installation partition. 

   hda1 /media/windows_backup
   hda2 /media/windows_xp

New slave hard drive containing any Linux installation that you desire.  

   hdb1 /ubuntu 
   hdb2 /linux swap 
   hdb3 /home
   hdb4 /extra partition for additonal Linux installation

Using a second hard drive you can just tell the Ubuntu installer to just use all of your new hard drive.

---

### Post by mrmonday on 2007-03-21
Also something I forgot to mention, there is a way of making windows/restore CD from your hard drive, I will have a look now for you.I also recommend what tcrroadie said, because you don't have a windows CD, just to be on the safe side. If something went wrong, you could be left with no operating system. This is unlikely, but could happen.

---

### Post by FlyingIsFun1217 on 2007-03-21
I would love to buy a second hard drive, and alas, I would love to make a backup of windows, but this is beyond what I can do.

I will try installing as the method I found described. If it deletes or screws up windows, it's no big deal (I only use it for gaming and what not), and I'll find a way to get windows...

Thanks!
FlyingIsFun1217

---

### Post by al7kz on 2007-03-21
edit

---

### Post by LuxVoodoo on 2007-03-21
> **FlyingIsFun1217 said:**
> It seems I have found some crude directions at [http://news.softpedia.com/news/Dual-Boot-Ubuntu-and-Windows-47701.shtml](http://news.softpedia.com/news/Dual-Boot-Ubuntu-and-Windows-47701.shtml) about how to partition the drive right to install ubuntu without disturbing windows. Here's what it says:

1) Defragment Windows
2) Use installer, when at partitioning screen, select 'resize IDE1 master and use free space'
3) Tell it how much space is to be used for the linux partiton
4) Install, reboot, and everything is good through GRUB

This will work, right?

Thanks a million!
FlyingIsFun1217


Actually, this is *exactly* how I did it on my HP machine.  I have a HP Pavillion Slimline s7320n, that has a 200 GB hard drive with two partitions on it.  The C: drive being my Windows XP partition and the D: drive being my Windows XP restore partition.  When I installed Ubuntu, I told the installer to resize and use free space. I didn't touch the slider to adjust the size. I just let it divide the free space 50/50 between Windows and Ubuntu. So when I boot through GRUB, I have my choice of Ubuntu, Windows XP, or Windows XP restore.  The process  didn't mess anything up and everything has worked fine ever since.  Ubuntu will need a lot of tweaking per your needs, but for someone like me who loves to mess around with programs, the alternative OS is one big project I always enjoy coming back to.

---

### Post by FlyingIsFun1217 on 2007-03-22
SO glad to hear, it seems that you have an almost identical setup to what I have (and will have :D).

Thanks again for confirming this for me, and yes, I LOVE to customize everything ;D

FlyingIsFun1217

---

