---
title: "gparted problem I think."
date: 2014-03-26
forum: General Help
---

### Post by keith14 on 2014-03-26
Hi,
I'm not sure that I' posting this in correct place but I used gparted to split my drive up into 3 partions. c: was the origional then added E: as extended and f: as a logical part. The trouble is I can see files in ksh window that do not show up in windows on the f: partition. using ls -lst these files are displaed as: 0 drwxrwxrwx   1 <unavail>       <unavail>             0 Jul 13  2009 PerfLog what does <unavail> mean?
Did I partition incorrectly?
Thanks,
Keith

---

### Post by oldfred on 2014-03-26
Windows does not correctly see Linux formatted partitions. Do not use Windows on Linux partitions. 
Best to only use Windows partition tools to shrink Windows and use gparted or command line tools in Linux to do all other partitioning tasks.
Windows may also convert from basic to dynamic partitions which will never work with Linux.

Post this from live installer.

sudo parted -l

---

### Post by keith14 on 2014-03-26
Wow seems like I made a mess of things. Thanks for getting back. I'm a little confused. what should I do to correct things?

---

### Post by Impavidus on 2014-03-26
Tell us what you want and tell us what the situation is now. For that last part, run oldfred's command.

---

### Post by keith14 on 2014-03-26
OK, I'm not running ubuntu from this pc. I do on other pc with win8 as organized by iso I down loaded from site. Sorry but I managed to do the wrong thing with a lot of thought and now have little confidence that I know the correct direction from here. Is the c: drive still ok? Or have I messed that up also?

---

### Post by Mark Phelps on 2014-03-26
> other pc with win8 as organized by iso I down loaded from site

What does this mean?  DId you download Win8 from somewhere on the Internet (e.g., Warez site) and are using that?

IS this the OS that you are asking about regarding the "C:" drive?

---

### Post by keith14 on 2014-03-26
Hi,  the pc I have problem with is not the one I have dual boot of win8 and ubuntu. I have other pc that initially contained xp and ran MKS toolkit. xp support ends in April so I wanted to upgrade to win7. I don't like win8 very much. So I did the wrong thing used gparted to resize c: drive and created E: ans F: drives. the c: drive was copied to e: and I also loaded win7 on f: partition. The copy of c: reduced part to e: part was done for back-up. I use gag to select boot-up and it all seemed to work out until I noticed that the files on the f: part were not reported correctly. I don't know what I should do now. I made a mess of things and would like to correct with least amount of work.

---

### Post by Navneet_Kumar on 2014-03-27
It would be more helpful if you can elaborate you problem a bit.............otherwise boot from a live iso of gparted...........

---

### Post by keith14 on 2014-03-27
the problem  is win7 is not showing all the files in F: partition. win7 boots cause xp is the primary (C:) partition. XP boot looks like it did prior to re-part. when the win7 boot is selected all looks like win7 and win7 disk manager shows 3 good partitions (they also check good). It's just that some files are not shown in windows. but I can see them doing: ls -ls. I using mkstoolkit for the unix commands which gets loaded on a dos or win partition.
I did use gparted live to reduce c: size and add E: and F: gparted is also happy with the partitions and they check good as well.
I think that should proceed with the current install of win7 that the reporting discrepency will cause many issues.

---

### Post by Impavidus on 2014-03-27
So you're not only on an NTFS file system, but you also use commands that have been tweaked to run on a Windows system. That explains the strange output. On the position of the owner and group of the files it says <unavail>, which is because ntfs doesn't support owners and goups the way linux does. As it's not even mounted on a Linux system, you don't even have a fake owner or group.

It looks like an empty directory. Maybe it has something to do with some Windows internal, hidden from view in the Windows UI. A Windows specialist may know. In any case, Windows 7 likes to (re-)format it's own partition, instead of using partitions it got from gparted.

---

### Post by keith14 on 2014-03-28
Yes, mks has been around  since dos. I'm not sure of their status today, last purchase was 02 I think. 
OK, I'm on win7 site trying to understand same.
New thought: I don't recall reformatting, I did specify NTFS. In dos/win world format is a very lengthy process which I didn't re-visit. The whole drive was NTFS and I just made 2 additional parts and specified the same partition type. 
The xp (origional part) seems to be same It's only 7 that having trouble seeing files that ksh in mks can see, and they are there. It also is root problem I've not noticed it in subdirs. Hmm, you've given me a new thought path.

---

### Post by keith14 on 2014-04-02
Hi,
completed install of win7, also have linux mint on same disk. The boot uses win7 boot loader but could use grub. I tried gag40 and it behaves like the rest. they all work. There are protection "features" associated with win7 and up that do not allow you to own your own install. please read  [http://answers.microsoft.com/en-us/windows/forum/windows_7-files/invisible-files-and-or-folders-in-windows-7/d73dd67c-f7d4-4d2d-886e-b774141bd24f](http://answers.microsoft.com/en-us/windows/forum/windows_7-files/invisible-files-and-or-folders-in-windows-7/d73dd67c-f7d4-4d2d-886e-b774141bd24f) if interested. So I'll close this post. Thanks for your interest.

---

