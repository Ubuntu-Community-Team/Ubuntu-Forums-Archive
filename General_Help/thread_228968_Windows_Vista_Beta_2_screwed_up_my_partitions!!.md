---
title: "Windows Vista Beta 2 screwed up my partitions!!"
date: 2006-08-03
forum: General Help
---

### Post by chien on 2006-08-03
I tried installing windows vista into one of my NTFS partitions. My Hard disk is running with RAID. As usual with windows, after successfull installation, i got the blue screen while booting vista for the first time. To my surprise, the problems didn't end up there, All my partitions got messed up! my boot partition which was sda6 is GONE! I runned my live cd and tried to mount my boot partition sda6, it mounted successfully and when i got to see the content of it, it was actually the files that were on sda7 before so in summary:

before vista:

sda1 = windows xp
sda2 = ubuntu
sda3 = fat32 (mainly contains video and mp3s)
sda4 = NTFS partition (tried to put vista here)
sda5 = linux swap
sda6 = boot partition
sda7 = fat32
sda8 = fat32

after vista:

sda1 = windows xp
sda2 = ubuntu
sda3 = fat32 (mainly video and mp3s)
sda4 = GONE!
sda5 = linux swap
sda6 = has the content of sda7 !!!!
sda7 = has the content of sda8!!!!
sda8 = can't access (its not letting me mount)

With the live cd i manage to recover grub and now i have my ubuntu running without X. However, i have no clue of how to recover back my windows xp, PLEASE SOMEONE HELP ME!!!

I tried to do a clean installation of windows, but XP is not detecting my partition, it only gives me the option to format the whole Hard disk! if i do so, i would lose all my files! so im in serious trouble now. 

ANY HELP IS APPRECIATED AND WELCOME!

Thanks!

---

### Post by Cure777 on 2006-08-03
Sadly, Vista beta 2 does that. When I used it, it screwed up my XP partition so badly (when i ran a chkdsk) that my only option was to reformat my hard drive. Sorry :(

---

### Post by teasum on 2006-08-03
Not sure if this will help, but you might want to try running a utility called 'testdisk' before reformatting or anything else.  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It's designed to recover partition tables, so it's worth a shot.  Just be sure to read the documentation on the wiki site before running it.

Good luck!

---

### Post by Subbu.exe on 2006-08-04
Well.. I Followed a Different Method for installing..

1) Install windows xp.

2) Install ubuntu, BUT Dont install the GRUB on MBR.. install it on /dev/fd0 (floppy)

3)Boot into ubuntu using that floppy and do this
**dd if=/dev/fd0 of=bootsect.lnx bs=512 count=1**
that makes a 512Bytes bootsect.lnx, put that in a drive where windows can access it..

4)Boot into windoze and copy the file over to windows root drive (C: )

5)type **notepad c:/boot.ini** in Start->Run.

6)Add This Line at the end of it **c:\bootsect.lnx="Ubuntu Linux"**

7)Try Booting into ubuntu thru NTLDR ;)

8 ) Install Vista.. It'll Even Considerately add Ubuntu into its new Menu :D


(PS-> Do Make all the Partitions Before Installing Anything..)

---

