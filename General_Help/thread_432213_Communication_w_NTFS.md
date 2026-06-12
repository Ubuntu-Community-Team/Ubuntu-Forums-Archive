---
title: "Communication w/ NTFS"
date: 2007-05-03
forum: General Help
---

### Post by xi_Slick_ix on 2007-05-03
hi - this post may be a massive repeat, i apologize ahead of time - and yes i did search some on the forums before posting...

I'm running Ubuntu 6.10, Windows XP home, and Windows XP 64 ed. Pro.  My concern is making Ubuntu @ least read from (and if possible write to) the NTFS windows partition (same 80gb maxter hard drive, ATA connection).  I basically keep all my music in a location in winDoze (spelled exactly like that whether you knew or not) folder readily accessible to iTunes for my brothers iPod, but all the music is standard MP3 format.  

I would like Ubuntu to be able to @ least read from that folder location so i can have my music while working in Ubuntu.  I realize that i could move the music to a standard fat32 partition and probably have it work seamlessly, but i really don't want another partition on the drive.

Any coding, 1st, or 3rd party programs suggested are much appreciated.  Thanks for you time!

---

### Post by qpwoeiruty on 2007-05-03
My NTFS partitions auto-mounted when I installed Feisty but in edgy I needed ntfs3g

Check out [UbuntuGuide](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows). That´s the first place I go to figure out things I want to do, and your question is answered there too (I know, that´s where I first found it :) ) 

ntfs-3g is read/write to NTFS :)

---

### Post by xi_Slick_ix on 2007-05-03
OOPS - i made an error in my description - Ubuntu is on a second 40gb HDD - w/ about 20 gb or so for it, and 20 for expansion on the windows NTFS partion on the 80 (which is the entire 80 gb HDD)

Don't know if that changes anything or not - sorry for the inconvenience - thanks again to anyone with suggestions!

---

### Post by Espreon on 2007-05-03
1st upgrade 2 Fesity
2nd boot in2 Fesity
3rd goto Applications>Add or Remove Programs
4th type NTFS into the search bar
5th hit the checkbox next2 NTFS Configuration Tool and hit apply
6th after installing go2 Applications>System Tools>NTFS Configuration Tool and hit it
7th check both boxes and hit OK
8th reboot and enjoy

It worked 4 me

---

### Post by qpwoeiruty on 2007-05-03
It shouldn´t change anything. That will only affect what you put in for the location of the drive.
Depending on how it´s setup, you will be mounting /dev/hda1, /dev/hdb1, or /dev/sda1 most likely.

Anyway, [Here´s another thread with more detailed instructions if you´d like](http://ubuntuforums.org/showthread.php?t=217009)

That thread also has instructions on how to find out which is your NTFS partition so you won have to worry about it.

Ed: As Espreon suggested, it would be easier to upgrade to Feisty. It makes a lot of things easier to do than with Edgy

---

### Post by xi_Slick_ix on 2007-05-04
Alright well i upgraded in Fiesty - and i can see the windows partition, and navigate through my folders to the music location, but when i tell Music Player to use that location for the library, or when i tried to manually add music folders from there, music player does nothing.  On the library add (the initial setup/scan) it pinged my processor for a couple minutes and then just sat there.  

Any idea?

---

### Post by xi_Slick_ix on 2007-05-04
alright Never mind - got it fixed - had to enable mp3 codec - thanks everyone who posted

---

