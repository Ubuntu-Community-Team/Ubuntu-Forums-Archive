---
title: "delete ubuntu"
date: 2013-04-18
forum: General Help
---

### Post by gustaf1010 on 2013-04-18
So i'm just done with linux. I posted on here and got no help with my graphics issue so all i want is it off my pc and my 1 tb hdd back. I have a dual boot win xp and ubuntu. I do not have any recovery disc for xp. I have xp on a maxtor 40 gb hdd and i used my 1 tb hdd for ubuntu thinking it would be great but it turned out to be a pain more then anything. All i want is ubuntu gone and my 1 tb hdd accessable to windows xp again. I have ubuntu 9.10 installed and the desktop disc for it. I have no internet on my pc only on my android phone. Any help would be apprecieated.

---

### Post by AmbiguousOutlier on 2013-04-18
It's a shame you can only use 9.10 can you not ask a friend if you can download the latest version using their connection, your machine is still good enough to run 12.04 LTS?

What happens when you boot XP? Can you not right click the drive from explorer and click format?

---

### Post by slickymaster on 2013-04-18
> **gustaf1010 said:**
> So i'm just done with linux. I posted on here and got no help with my graphics issue... 

Maybe it was just bad luck. Don't you feel like give it another shot and wait before going on so drastic as to uninstall Ubuntu?
I'm sure this time someone will for sure try to help, at least.
> **gustaf1010 said:**
> so all i want is it off my pc and my 1 tb hdd back. I have a dual boot win xp and ubuntu. I do not have any recovery disc for xp. I have xp on a maxtor 40 gb hdd and i used my 1 tb hdd for ubuntu thinking it would be great but it turned out to be a pain more then anything. All i want is ubuntu gone and my 1 tb hdd accessable to windows xp again. I have ubuntu 9.10 installed and the desktop disc for it. I have no internet on my pc only on my android phone. Any help would be apprecieated.
Well, if you really feel like it's the only possible thing to do...
Tell us, how was Ubuntu installed on your computer? Did you install it on a prior windows computer?

---

### Post by gustaf1010 on 2013-04-18
I don't think i can use the newest version. I'm running an old pentium 4 with hyper threading. On top of that i ccan't find a reliable way to install my graphic driver without internet access. Anyway when i boot windows it just gives me my c drive which is my 40 gb hdd it doesn't show my other hdd at all. I believe it has to do with that drive being ext4 and windows xp pro not being able to read it.

---

### Post by gustaf1010 on 2013-04-18
My problem is my graphics driver i spent a good 8 hours last night looking for a way to install it by downloading the software on my phone transfer it to ubuntu and then install the driver. When i found a way to do so it involves killing the x server and running the file in the terminal that takes up the whole screen and when i did so it just opened the directory instead of running the file. And yes my pc was running win xp pro sp3 before i even thought of ubuntu. I read a few posts online and figured there was enough support out there for games using wine by now that i'd give it a shot. But since i can't install the proper linux driver and i can't get any help on my other thread i just want to go back to playing games on windows.

---

### Post by AmbiguousOutlier on 2013-04-18
Use a program in windows to be able to view ext4;
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Or do you have gparted to reformat it for ntfs?

---

### Post by t0p on 2013-04-18
> **gustaf1010 said:**
> I have no internet on my pc only on my android phone.

Unfortunately, Ubuntu works at its best when it can access the internet.   A constant connection is not required, but it does like to check to see if there are any problems and grab the fixes (automagically via Update Manager).  You not got a local McDonalds or KFC or suchlike, with free wifi for customers?  Go buy a coffee, then sit down with your laptop and see what's what.

If you have a desktop machine, get a power inverter, throw the computer into the back of a van (windowless so they can't see what you're doing) and deal with it that way.

 But remember: Windows like the internet too.

Good luck!

---

### Post by gustaf1010 on 2013-04-18
I download ext2fsd and installed it but it doesn't show the hdd in my computer just in the program. Is there a way to format it from the program?

---

### Post by AmbiguousOutlier on 2013-04-18
You should be able to mount it, according to the FAQ's;

[i]
   "Just "right click" on the dialog list, and select "Change Drive Letter".
   Then you'll see the mount point dialog, you can add, change or remove
   any driver letters."[/i]

---

### Post by afoin on 2013-04-18
If you format your Ubuntu hd you will probably not be able to boot XP. You first have to fixmbr first, usually with XP install cd.

---

### Post by BlinkinCat on 2013-04-18
> **afoin said:**
> If you format your Ubuntu hd you will probably not be able to boot XP. You first have to fixmbr first, usually with XP install cd.

+1

---

### Post by gustaf1010 on 2013-04-18
I would just be able to switch my boot option from the bios menu. Ubuntu is on a different hdd then windows. And i tried formatting it after i got it mounted but it said the hdd is write protected. Is there a work around?

---

