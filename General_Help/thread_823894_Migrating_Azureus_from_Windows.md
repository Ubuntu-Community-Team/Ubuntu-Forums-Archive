---
title: "Migrating Azureus from Windows"
date: 2008-06-09
forum: General Help
---

### Post by Secret-HQ on 2008-06-09
Hi, all —

Ubuntu newbie here, interested in porting over Azureus from a Windows PC to one running U8.04.  I have plenty of comments, notes, categories, and custom names on my torrents in Azureus, and on a Windows machine I'd just port over my entire settings folder (from Application Data).  Is there a way to get these settings into my fresh Ubuntu installation of Azureus?

(Keep in mind that I'm pretty green, and I'm not even sure how the file structure works on Ubuntu — and I only know four or five CLI commands!  :D)

Should I consider running Azureus in Wine?  Would that allow me to port over the Windows settings files, and is this really as goofy and useless an idea as it seeems?

Any help or advice is greatly appreciated, of course!

---

### Post by cozmicharlie on 2008-06-10
Not sure if you can do this.  Azurues is written in Java so it is independent of the OS.  You could try it.  I know in Linux Azureus stores the config in /home/yourname/.azureus.  This is the default home folder.  You must open the file manager then under view check "show hidden files".  I don't have Azureus on windows so I do not know if the file structure for the config is the same. 

I do know this - don't run Azureus under wine.  If you want to keep your settings you would be better of settng up XP in Virtual Box and migrating your Azureus to XP in Virtual Box.  It is very easy in Linux to set up.  Or, to try this out you could set up Ubuntu in VB then install Azureus and see if you can migrate your settings.  That way you don't lose your XP if it cannot be done.  Another option I have done on one of my laptops is install Hardy using Wubi.  This installs Ubuntu just like any other program on Windows so you don't have to dual boot.  When you install Wubi it gives you an option at boot up to run Windows or Ubuntu - it is slick and a good first step to get introduced to Ubuntu.  That way you could play around with Azurues under Ubuntu but stil keep your XP set up so you don't lose the settings.

Good luck

---

### Post by Secret-HQ on 2008-06-10
Thanks, Charlie!

Believe it or not, I really was stuck at the simple step of not knowing where the config files were kept — so I installed Azureus, loaded a torrent file and went looking.  Once I realized where the config files were stored (and that they were in a hidden folder!  :D) I was able to bring over my Windows settings lickety-split.

Of course, all my files still point to Windows-style directories (e.g., T:\torrents\category\file.ext).

Could I set up a "T" NTFS drive in Ubuntu and just move my files there, I wonder?  If you partition a drive in Ubuntu as NTFS file system, can you give it a Windows letter (and will Azureus under Linux be able to find it)?

Utter newbie stuff here — but it's fun to sart somewhere, I suppose.  If anyone wants to chime in and educate me, I'd sure appreciate it!

---

### Post by cozmicharlie on 2008-06-11
> **Secret-HQ said:**
> Thanks, Charlie!

Believe it or not, I really was stuck at the simple step of not knowing where the config files were kept — so I installed Azureus, loaded a torrent file and went looking.  Once I realized where the config files were stored (and that they were in a hidden folder!  :D) I was able to bring over my Windows settings lickety-split.

Of course, all my files still point to Windows-style directories (e.g., T:\torrents\category\file.ext).

Could I set up a "T" NTFS drive in Ubuntu and just move my files there, I wonder?  If you partition a drive in Ubuntu as NTFS file system, can you give it a Windows letter (and will Azureus under Linux be able to find it)?

Utter newbie stuff here — but it's fun to sart somewhere, I suppose.  If anyone wants to chime in and educate me, I'd sure appreciate it!

So it ever is - we all get stuck at the simple steps because they all are simple once someone shows us how to do it.

You can partition an NTFS partition in Ubuntu.  Ubuntu now has native support for ntfs.  Alternatively, you could just change the config files to point to a different folder in the Ubuntu file system.  I would think you could do this right from the Azereus menu>tools>options.  Make sure you are in advanced mode and you can change the files right from there.  This should work but if not then you can create an ntfs partition but I don't think you need to.  Try it and let me know how it worked for you.

---

### Post by Secret-HQ on 2008-06-12
> **cozmicharlie said:**
> So it ever is - we all get stuck at the simple steps because they all are simple once someone shows us how to do it.
Too true!  :D

> **cozmicharlie said:**
> you could just change the config files to point to a different folder in the Ubuntu file system.  I would think you could do this right from the Azereus menu>tools>options.
That's what I'm trying to avoid, since I have so many torrents pointing at different paths on the same drive.  (e.g., T:\my torrents\ebooks\ubuntu\file.ext).  I'd like to preserve the subdirectories without having to edit each and every torrent — so what I'm hoping to do is create an NTFS partition, call it "T:" (a Windows letter) and port over all the existing data and torrent files to the Ubuntu box as-is.

Another idea is that I could run Azureus from the Windows partition on this box or from the Linux partition and still be working from the same pool of data and torrent files, switching between both pretty seemlessly, depending on whether the machine needed to be running in Windows or Ubuntu for different things.  (This would also give me some good setup for comparing performance in the two environments — I hope.)

Thanks for all your advice, Charlie — please feel free to chime in again!  (Hopefully I can find time to sit down and spend more than half-an-hour on this soon and get the Ubuntu box all set up.  Right now I'm having some trouble getting into it via Xming, so I'm going to tackle that problem first, then try the repartitioning — unless someone chimes in and explains why it's a terrible idea!  :P)

---

### Post by cozmicharlie on 2008-06-12
> **Secret-HQ said:**
> 

That's what I'm trying to avoid, since I have so many torrents pointing at different paths on the same drive.  (e.g., T:\my torrents\ebooks\ubuntu\file.ext).  I'd like to preserve the subdirectories without having to edit each and every torrent &#8212; so what I'm hoping to do is create an NTFS partition, call it "T:" (a Windows letter) and port over all the existing data and torrent files to the Ubuntu box as-is.

Another idea is that I could run Azureus from the Windows partition on this box or from the Linux partition and still be working from the same pool of data and torrent files, switching between both pretty seemlessly, depending on whether the machine needed to be running in Windows or Ubuntu for different things.  (This would also give me some good setup for comparing performance in the two environments &#8212; I hope.)

Thanks for all your advice, Charlie &#8212; please feel free to chime in again!  (Hopefully I can find time to sit down and spend more than half-an-hour on this soon and get the Ubuntu box all set up.  Right now I'm having some trouble getting into it via Xming, so I'm going to tackle that problem first, then try the repartitioning &#8212; unless someone chimes in and explains why it's a terrible idea!  :P)

When you say torrent files do you mean the torrent files themselves or the music files?

Are you trying to set this up as a network?  If so you could leave Azureus on your windows box and add Azmrc (a plug in for Azureus) to your linux box.  Azsmrc is slick because it allows you to have complete control of Azureus from any networked computer.  For example I have Azureus set up on an old laptop running Ubuntu.  I have Azsmrc set up on another Ubuntu box, a Windows box and a Mac.  I can access Azureus from any of those computers using Azsmrc with full control over Azurues and download from any of them to the ubuntu box with Azureus.  I can choose to leave a copy of the torrent on the box I am working on or not (it always saves the torrents to the Ubuntu with Azureus).  The music files download to my Ubuntu with Azureus and I access them via ssh (I use tunnelier for ssh on my windows computer and open ssh on Ubuntu- it works great). Alternatively you could set up as a server so you don't have to move files around.  I set up another plug in for outside access through the internet.  All this can be done with Azureus and it's plug-ins.

---

### Post by Ender305 on 2008-06-12
I'm afraid you can't do that, the way linux manages extra partitions and drives is way different that the way windows does it, in linux, every mounted partition or drive(other than the root(/) partition) is named in /media/ the /media/"name" is the same as the drive letter in windows, so I guess you could make a new partition and edit the beginning of every torrent's path, but if you're already going to so much trouble, just make a folder like /home/[yourname]/Azureus and arrange them all in there

---

