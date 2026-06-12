---
title: "SD Card Says Its Full"
date: 2007-08-05
forum: General Help
---

### Post by covert215 on 2007-08-05
I mounted a 2GB SD memory card to put some music on it.  I put some stuff on it, but now it won't let me.  It keeps saying "there is not enough space on the destination." However, nautilus says it has 970 MB left on it.  Does anyone know what to do?

---

### Post by Swarms on 2007-08-05
Hmm don't know if it works, but when I use my phone for storaging music and I delete it afterwards, it just moves it to a hidden folder in parent directory named like .beartrash or something similar, when I delete that I get a lot of space.

---

### Post by covert215 on 2007-08-05
Ejecting and remounting fixed it for one file, but then the error reappeared.

---

### Post by covert215 on 2007-08-05
Apparently, there were 2 1gb partitions on the card.  Its a common problem w/ 2gb SD cards.  I reformatted it as one and it seems to be working now.  However, it causes issues with my XP computer...

---

### Post by pickarooney on 2007-12-31
I have this same issue in that my 2GB card says it's full after 670MB of files copied. I assumed there was some sort of trash folder but can't find one. When I first bought it, it was full of a heap of crap for what appeared to be GPS systems, so they could have formatted it anyy old way. 

So, how would I go about formatting it completely?

---

### Post by pickarooney on 2008-01-01
Well, using **mkfs -t vfat /dev/sdb1** I managed to clear up the space on the card, but now my car radio says the SD card is empty. Nutsacks.

---

### Post by kvonb on 2008-01-01
-

---

### Post by pickarooney on 2008-01-01
Meh, don't have access to any Windows PCs with an SD card reader. The card mounts fine and is r/w, but maybe by radio has a problem with cards above a certain size.

[edit]
Sometimes the answers are right in front of you... I put the card into my digital camera and formatted it with that, then copied some music over and the car stereo reads it fine.

There's something odd with these cards though, at times copy speeds are upwards of 2.5MB/sec and at others it drops to 10kB, often between two files of similar size in the same directory.

[edit2]
and it's back to square one, the card claims to be full after 35%. What a rip-off! :(

---

### Post by John_T on 2008-05-16
It could be related to the VFAT system, rather than something more nefarious.

I had a similar problem trying to transfer 300 jpeg files totaling less than 21 MB onto a 1 GB SD card.

Put 'em all into a subdirectory on the card and there was no problem.

Cropped from various sections of the [wikiepedia entry]("http://en.wikipedia.org/wiki/File_Allocation_Table#Long_File_Names_.28VFAT.2C_LFNs.29"):

> One of the "user experience" goals for the designers of Windows 95 was the ability to use long filenames (LFNs&#8212;up to 255 UTF-16 code points long), in addition to classic 8.3 filenames. LFNs were implemented using a work-around in the way directory entries are laid out (see below). The version of the file system with this extension is usually known as VFAT after the Windows 95 VxD device driver, also known as "Virtual FAT" in Microsoft's old document.

...

Long File Names (LFN) are stored on a FAT file system using a trick&#8212;adding (possibly multiple) additional directory entries into the file allocation table before the normal file entry. The additional entries are marked with the Volume Label, System, Hidden, and Read Only attributes (yielding 0x0F), which is a combination that is not expected in the MS-DOS environment, and therefore ignored by MS-DOS programs and third-party utilities. Notably, a directory containing only volume labels is considered as empty and is allowed to be deleted; such a situation appears if files created with long names are deleted from plain DOS.

Dig into the details and you realise that a bunch of long file names can rapidly chew into your available FAT space, resulting in "out of space" type errors long before the media is actually full.

I think it was a post on a MEPIS board that led down this track.  Yep, [here 'tis]("http://www.mepis.org/node/14004").  Thanks EnigmaOne.

---

