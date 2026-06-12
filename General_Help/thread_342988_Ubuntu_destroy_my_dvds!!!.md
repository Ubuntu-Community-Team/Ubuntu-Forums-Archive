---
title: "Ubuntu destroy my dvds!!!"
date: 2007-01-20
forum: General Help
---

### Post by ryghar on 2007-01-20
Trying to mount dvds I try many diferent fstab options thinking that theres the problem but.... when i try the dvds used in the test in my dvd player or in windows there was blank!!!

Some test later my conclusion is> Ubuntu destroy my dvds (all dvds was dvd movies copies)

My fstab is:

UUID=84600014-01d1-4216-8e4e-fda75f6caf1e /               ext3    defaults,errors=remount-ro 0       1
UUID=02c46d11-89d4-41da-8d83-2e89e8b91232 none            swap    sw              0       0
/dev/sda1 	/media/windows  ntfs 	auto,ro,exec,users,dmask=000,fmask=111,nls=utf8  0       0
/dev/hdb        /media/cdrom0   auto user,noauto     0       0

Im using edgy. The dvd unit is a LG DVD recorder.
With cd's or data dvds have no problems.
I have the "restricted formats" enabled

Please help!! I destroy 6 movies allready.](*,)

---

### Post by ryghar on 2007-01-20
Anybody? or please if someone can play and copy movies dvds post the fstab config to try.

Thanks

---

### Post by 3rdalbum on 2007-01-20
It is impossible for any operating system to "destroy" your DVDs. Are you absolutely sure they were working BEFORE you put them into your drive?

I added an LG DVD burner to my computer - you don't need to change your fstab, Ubuntu will mount the disc automatically, even if you don't have the Restricted Formats stuff installed.

---

### Post by ryghar on 2007-01-20
Im absollutly sure. After realize whats going on I cant believe it too. So i try again with a dvd that was running on my dvd player and after mount the disc was blank.....

When I mount the dvd it does correctly but I cant play it. The system goes slow and I ended ejecting the disc. When i try to mount it again ubuntu said that the dvd is blank *it offers me to make a dvd or ignore" a select ignore and eject the disc. When I try it again in my dvd player the disc was blank (ofcourse is not blank, but i is no readable by anything)

My ubuntu must be writing something to the disc. I cant figure out why.

Cant you post your fstab config to try and keep troubleshooting this?
mtab cant couse some problems?

---

### Post by zekopeko on 2007-01-20
fstab is only for HARD disk drives as far as I know.

DVD doesn't fall in that group

---

### Post by ryghar on 2007-01-20
The entry in fstab for /dev/hdb was there from ubuntu instalation. I only do modifications to that line because I was not able to play dvds.  /dev/hdb is my dvd device so.... 

Any ideas? fstab example of a working play and copy dvd instalation?

---

### Post by ryghar on 2007-01-21
Please... just a hint

---

### Post by bulldog on 2007-01-21
Can't believe they're erased,maybe ubuntu can't read them,but your data is still there.
Try them with windows and you'll see the DVD is intact.

Only a burner program can write to your DVD's, not Mplayer or what ever you use to look at them.
So I'm pretty sure your DVD's aren't destroyed,only ubuntu can't read them for some reason.

---

### Post by Ramses de Norre on 2007-01-21
> **zekopeko said:**
> fstab is only for HARD disk drives as far as I know.

DVD doesn't fall in that group

fstab is for all mounted filesystems, including cd-rom and floppy drives.

My fstab entry for my dvd recorder is ```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I think your "auto" parameter should be a filesystem indication (for dvd iso9660), and that could be the reason why it isn't working.

---

### Post by rai4shu2 on 2007-01-21
Most likely what happened is that your drive has malfunctioned. My advice is to take it to a professional repair service.

---

### Post by ryghar on 2007-01-21
Bulldog: I try the dvds after in windows and dvd player and are blank....
Ramses de Norre: thanks, i will try that. 

The drive works well in windows.

---

### Post by kuja on 2007-01-21
I used to have a problem similar to this ... other times it would seem to burn it ... the I could see that files were there, I just couldn't view them ... turned out my burner had went crap on me. The only thing you can do is have it repaired or get a new one, most likely.

---

### Post by ryghar on 2007-01-22
Ok, to confirm what ubuntu is the dvd killer....
I try read and copy dvds in windows and everything works ok.
I modified the fstab in ubuntu and do another test....

The dvd was destroyed again!!!!!

What is happening??? 

Now Im trying di read the destroyed dvds from another PC with the software IsoBuster (a dvd recover).
The disc is not readable anymore..This is what isobuster said:

How can I "reinstall" everything about dvd drive? Icluding the drive "driver" itself? A dont want to reinstall everythig (this is not windows, I dont wanna do that)

---

### Post by rai4shu2 on 2007-01-22
Sorry, but I don't follow anything you're saying. Please state clearly in detail the steps you are following in Ubuntu.

---

### Post by 454redhawk on 2007-01-22
> **rai4shu2 said:**
> Most likely what happened is that your drive has malfunctioned. My advice is to take it to a professional repair service.


At $28 a pop just get a new one.

---

### Post by goatflyer on 2007-01-22
ryghar: iso buster is saying that the localization info on the dvd can't be read.

Lets proceed with the hypothesis that the linux driver installed for your dvd is either wrong or wrongly configured, and is somehow telling the hardware to overwrite or reburn.

Let's try changing your /etc/fstab entry for the dvd to this:

/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0

(added the 'ro' mount option, it means read-only)

and then reboot (including power on/power off) just be sure that all old stuff is forgotten.

Then restart with nothing in the dvd drive, re-look at your /etc/fstab to make sure the 'ro' change is still there, then try inserting another proven-good-but-possibly-soon-to-be-trashed dvd.

---

### Post by Kulgan on 2007-01-22
I had a similar issue when burning stuff to a DVD. It screwed things up, and became unreadable (would give me "media not present" and all that). But it's not all that bad - I can still read things properly, and as far as I know, I can still burn CDs. 

I doubt it has anything to do with the drive, though...

-K

---

### Post by ryghar on 2007-01-22
I will try the ro thing.

The problem must be related to dvd format. I can mount and read cd`s (files, mp3 and divx files) and data dvd´s perfectly. When I insert a dvd totem comes to life, hangs, and bye bye dvd....
How can I change the default app to launch when insert a dvd? Maybe is totem who trash the disc.

---

### Post by ryghar on 2007-01-22
More info.... with original dvd works ok!! The problem are only dvd-r with movies.....
Something is writing the disk when its mounted....with the original works because it cannot write the disc.
The question is... what can be doing this....and why....

---

### Post by ryghar on 2007-01-24
Its working!!!!! yesssssss !!!

Well.. looking for the solution I saw many people with this same problem and none solution, so , this is what it works for me:

I really made 2 changes at the same time and I dont know which solves the issue.

First I put the ro in /dev/hdb is fstab like suggested in this post. Sounds rare...I put the ro but i still can write to the drive.....
Then download the source of [libdvdcss 1.2.9]("http://download.videolan.org/pub/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.gz"). In the package theres a Install text file, follow the instructions to compile for debian.
After that reboot and enjoy!!

I try totem, vlc, copy a dvd-r from another and make a backup to dvd with mondorescue. All working perfectly.

Thanks to all for the support.

---

