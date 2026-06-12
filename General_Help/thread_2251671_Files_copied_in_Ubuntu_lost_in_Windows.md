---
title: "Files copied in Ubuntu lost in Windows"
date: 2014-11-06
forum: General Help
---

### Post by briansherred on 2014-11-06
Hoping there's a simple fix for this.
Basically I screwed my boot loader and had to reinstall Windows. I had Windows 7 and Ubuntu dual booting and installed Windows 10 on another partition to try it out. This destroyed the boot loader irreparably.
I used Ubuntu in Live USB to copy the files from the Windows 7 partition to another drive and partition. It took about an hour or so and I confirmed the files were copied and accessible in Ubuntu before I went ahead and reinstalled Windows (I went with Windows 8.1 this time) to the original drive and partition. When I tried to open the folder I backed everything up into, Windows couldn't open it and reported the folder as empty, and the drive's free space is much higher than it should be with the files copied onto it.

It really doesn't make much sense and Windows was very quick to install. Right now I'm running Photorec to try to recover the files, but it'd be nice if I could just get it all back without taking so much time trying to scan and recover them (and I can't say I'm too hopeful about file recovery since I haven't had good luck with it in the past).

Thanks in advance for any help!

---

### Post by wyliecoyoteuk on 2014-11-06
Have you tried booting a livecd to see if the files are still there?
if the drive is formatted as a liux filesystem, windows won't read it.

---

### Post by Bucky Ball on 2014-11-06
Also, I had a weird problem like this previously, but with XP. The files, for some bizarre reason, get marked as 'hidden' and Win won't see them even though Win will. 

Can't remember how I fixed. Was on my desktop. Will have a sniff around on it later.

---

### Post by ringstaart on 2014-11-06
If you still have Ubuntu installed, boot into that, and see if you can access the files. Otherwise, use a live cd.

If you manage to get to the files, put them on some external medium like a usb stick, and try to use that in Windows.

---

### Post by briansherred on 2014-11-06
Thanks for the fast replies! Turns out I was overly negative about the situation, they are still there when I access the folder in Ubuntu. They are on an NTFS drive, it's just that I created the folder they're in in Ubuntu.
I tried copying some of them to an external drive in a folder I created in Ubuntu and they're accessible there in Windows. There's quite a few files so it'd be nice to have them accessible in Windows without having to copy them again to an external drive.

EDIT: Turns out it should've been obvious to me what the problem was but it didn't occur to me because the files were accessible in Ubuntu, but while I was copying the files the transfer would lock up and Nautilus then Unity would lock up. I could still see and access the files, I'd have to just restart and resume copying the files and skip the ones already copied. I guess the directory info got corrupted so Windows couldn't see the files but Ubuntu still could. I ended up having to copy them out of the corrupted directory to a new one in smaller chunks and delete/re-copy groups of files whenever Ubuntu would lock up, all is well now though :)
I was running Ubuntu 32 bit from a Live USB installed with LiLi USB creator.

---

### Post by nerdtron on 2014-11-06
Also just a reminder when copying files to Windows filesystem, don't use the same filename with different upper case and lower case letters.

In Ubuntu **Sample.txt** is different from **sample.txt**. No problem here
In windows, when you open the folder containing those two files, windows can throw you some errors on that.

---

### Post by Bucky Ball on 2014-11-06
Good news. Please mark thread as solved. See the second link in my signature. Good luck. ;)

---

