---
title: "cd/dvd drive not opening"
date: 2007-10-25
forum: General Help
---

### Post by thinsoldier on 2007-10-25
If I start up with a disk in the drive Ubuntu will let me read the disk and I can open the tray to put a new cd/dvd in.

 But if I start up with no cd in the drive, my tray wont open. It was like this in the previous version also

---

### Post by mlissner on 2007-10-25
This is very odd. What happens if you type ```
eject
```

---

### Post by rundee_f on 2007-10-25
do u also use xp/vista? does the problem also occur on xp/vista?
considering hardware problems..

---

### Post by thinsoldier on 2007-11-13
Yes I dual boot xp and it's never happened in xp.

Entering eject into the command line does nothing.

I've tried a dozen or so cd's and dvd's both originals and burned cd audio, data cd, data dvd, dvd movies and about 75% of the time I can't see what's on the disk and the cd drive won't open.

All these cd/dvd work fine in windows.

---

### Post by thinsoldier on 2007-11-24
Update:

It's actually quite random when it decides to work.

The other day I used ubuntu and the drive worked fine the whole time. Then I rebooted and used windows and the drive continued to work as usual.

Today I used ubuntu again an the drive doesnt work. I rebooted with a disk already in the drive and it didn't read the disk. I see a cdrom icon on my desktop so I guess it mounted something but I can't see any of the files on the disk.

I rebooted with multple cd's & dvd's and it reads none but always shows the cdrom icon as if it mounted something.

I tried the same disks in windows. They all work.

I changed the dvd drive and ide cable. Same problem in Ubuntu. Everything works in windows.

I tried 2 more cd rom drives and 1 more dvd drive. Same problem in Ubuntu. Everything works in windows.


I think I may have found a possible source of the problem.
I have been using AcetoneISO2 to mount .bin files as drives and there has always been an icon in that program to indicate a mounted cd rom drive that I cannot unmount. Maybe this is the cdrom represented by the icon on my desktop and it interferes with the mounting of cds in my actual dvd drive?

---

