---
title: "Rescuing files from a Windows PC with Ubuntu: basic questions about the files"
date: 2021-01-28
forum: General Help
---

### Post by valdemarv on 2021-01-28
Hello, I'm rescuing a large number of files from a quite old Win 7 PC (from 2008 I guess) with the help of Ubuntu (live session, USB stick). There is something seriously wrong with the PC, since it almost every time freezes completely a few minutes after booting. I suspect one of the hard drives is about to break and hence I thought to rescue all data before the computer becomes completely unusable and move them the another (Win 10) PC. 

I intend to copy the files to an external usb drive that can be then attached to the new PC.

At least the first rescue session went fine and the machine did not crash copying files to the external drive. Since I'm not so familiar with the differences between Win and Linux/Ubuntu, especially regarding how they handle files, I'd need some help with the following concerns:

1) When I copy the files with Ubuntu live, do they remain exactly the same or does the Win-Ubuntu-Win transfer somehow alter the file contents?

2) If they stay the same, does it also apply to program files (e.g. *.exe) or only data files? I need to rescue e.g. some old programs that run in Win without installation and it is necessary that they remain unchanged.

3) What about file permissions? I presume that all files in the Win7 machine have some defined permissions. What happens to the permissions in the transfer and will the new PC (Win 10) be able to use them?

4) Anything else relevant that I should take into account, especially compared with a situation where I would just copy the files using the original Win 7?

---

### Post by grahammechanical on 2021-01-28
1) To put your mind at rest, use a Ubuntu live session and see if you can read a Windows txt file. The use the live session to copy it somewhere and then see if it has changed in any way. I very much doubt that it will have changed. The information in documents is stored on a hard disc in digital form and it makes no difference to the information if the hard disc has a Microsoft partition system and format or Linux partition system and format.

2) On Linux we have a program called Wine. It lets us run Windows applications in Linux. I use it. I download the application's install file and use Wine to extract the application and then using Wine I run the the application's setuo.exe and the application installs in Linux and loads in Linux. I can even read the application's readme.txt file. So, I do not think that copying a programs Window's folder onto a Linux hard disc will alter things when you copy it back on to a Windows disc. Better to copy over the application's install file and re-install when back in Windows.

Regards

---

### Post by guiverc on 2021-01-28
If the system is freezing; I'd personally stop trying to get the data off.. and find the cause of the freeze.  

I'd boot & test the system using *live *media only, so nothing is corrupted on the disk, and not use the disk during the testing, so no harm is done to it.  Freezing reminds me of capacitor failure OR PSU issues, so I'd check those first (ie. open box & look, PSU tests take a little longer..)  If both are okay, then I'd do a memory test.

To get your data off, I'd remove the drive, and use it only on a *stable* system  (ie. I'd only use that system after you've concluded it's stable to ensure data doesn't get corrupted as you copy it off).  

I'd check the drive health first (on the *stable* system), using drive's SMART - [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) and from those results plan how you get the data off.  If the drive is near dead, go for the most valuable data first..   Checking SMART doesn't involve anything but reading the circuitry of the drive so won't do any damage allowing you to plan to ensure you get the most data off it you can.

Recovery of data should then occur, but I'd only do it on a stable system.

---

### Post by valdemarv on 2021-01-29
Thanks to both! I need to clarify that in this case there is no need to copy the files in-between to a Linux formatted drive, since both the hard disks in the failing computer and the external hard disk are Windows-formatted and have been attached to the computer for a long time already.

Copying and reading a text file goes fine.

So if I understand correctly, there is no known reason (deriving from the inherent properties of the two systems Win/Linux) for the files t change within such a copy operation (Win disk -> another Win disk) performed by Ubuntu live?

Concerning the overall process, I have opened the case and could not see anything obviously wrong in the capacitors or any other components. Some dust yes, but nothing spectacular. Both the CPU fan and case fan function. I am interested still to check various hardware parts to see if the computer can still be used for some less demanding purposes. Any hints about testing the PSU are welcome too, as are any other suggestions.

However, at this point I would prefer saving the files without moving actual drives. The case of the old computer is a bit difficult to work on, and since the Ubuntu live session worked without problems, I'm starting to think that perhaps the problem is in the "not-so-good-old" Windows drivers... I'm a bit pressed for time too so need to move files first and then check the computer at a later phase.

So do you think I can proceed with Ubuntu-copying without known problems?

---

### Post by guiverc on 2021-01-29
I've already said my piece.. 

Swollen capacitors are what you look for, many caps have a cross, or lines indented on the top of them, so as they swell, the lines that should be there disappear, before the swelling becomes more obvious.

 If you can't see, they are easy to feel anyway. They should be flat at the top (or all of the same brand/type indented identically); a 0.5mm rise is a big problem, so swelling doesn't need to be major; minor swelling tends to cause lock-ups.

You'll find loads of pictures on the web, though they're usually obvious ones (from machines that usually don't turn on; though even some obviously swollen ones do still function (most of the time).

Files copied will copy correctly. I'd only suggest remembering to preserve file attributes if you want/need them, but that's the same in windows (only the defaults for each OS differs).  ie. you might want to know when the file was last modified; not as much when it was copied.. (meta data can vary across file-systems, but if your source & destination drives are the same format, I'd not expect any loss of meta-data/file-attributes).

---

### Post by Impavidus on 2021-01-29
A file is just a sequence of zeros and ones. Copying it doesn't change that sequence. File type doesn't matter; as far as the file copying tool is concerned, all files are equal.

Permissions however are not retained. Linux and Windows don't understand each other's permissions. Permissions are stored separate from the file contents.

---

### Post by valdemarv on 2021-01-29
> **guiverc said:**
> Files copied will copy correctly. I'd only suggest remembering to preserve file attributes if you want/need them, but that's the same in windows (only the defaults for each OS differs).  ie. you might want to know when the file was last modified; not as much when it was copied.. (meta data can vary across file-systems, but if your source & destination drives are the same format, I'd not expect any loss of meta-data/file-attributes).

Thanks to both @guiverc and @Impavidus! Very useful info. I realize that I forgot about file attributes. May I still ask what you mean with this quote above? I mean what do you mean by "remembering to preserve file attributes"? If I just drag them from one win drive to another, are they preserved by default when I use the Files window in Ubuntu?

---

### Post by guiverc on 2021-01-29
I rarely copy to & from a NTFS or a *foreign *(non-native) file-system, and sorry I don't use `nautilus` (or "*Files*" as it likely appears in your *unstated* release of Ubuntu in the GUI menu), so I don't know what its defaults are.

From command, I'd use the `-p` option with a `cp` (copy) command to ensure preservation of ownership, timestamp etc. details in the copy.

[[COLOR=#000000]@Impavidus' [/COLOR]]("https://ubuntuforums.org/member.php?u=1417721")comment was probably because of more experience (*especially recent; I no longer support windows systems*) with the copying to & from non-native (non-POSIX fully compliant) [I]file-systems.

[/I]If it was me, I'd copy a file (using your preferred method, `nautilus` for example), then look at the results and check it does what you want.

(*I just loaded `nautilus` on my hirsute system, and sorry, I can't advice on it's use.. I've not used it in years*...)

---

### Post by rsteinmetz70112 on 2021-01-29
Excuse me for asking but what are you using to copy the files?

---

### Post by valdemarv on 2021-01-29
I'm using Ubuntu 20.04.1 LTS (live session, without installing). The "Files" is the program that opens when you click on the GUI the yellow folder-like icon. Dunno its real name.

---

