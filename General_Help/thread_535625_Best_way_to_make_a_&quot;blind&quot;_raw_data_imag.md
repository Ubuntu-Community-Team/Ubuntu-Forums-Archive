---
title: "Best way to make a &quot;blind&quot; raw data image of a CD?"
date: 2007-08-26
forum: General Help
---

### Post by notasquirrel on 2007-08-26
Hi, my searches aren't helping so far so I hope this is a quick question!

What method do I use to make a raw binary image of a CD that is a strange filesystem that no operating system understands normally?  Will dd work or do I need some commercial utility like raw-write?  (I don't have any of these or I'd make a sure-fire duplicate to begin with!)

I ask because so many utilities I've checked out so far want to be able to interpret the filesystem on the disk, and report errors when they can't find a folder tree to work with.

I need help because I won't be able to see if the image file I made worked properly until after I've solved a whole other set of problems for using the filesystem and its contents.  My friend wants his disk back soon, so if I use a bad method I no longer have a disk to try again with.


It's a CD of factory sample backups for the old ASR-10 and TS-12 music keyboard made by the now-dead Ensoniq.  (Killed by Creative Labs.)  I have the keyboard but lost the original factory patches in a cross-country move.  Part of my problem is I'm still searching for software to interpret the Ensoniq file system and let me recover the instrument samples, so I can't "experiment and see if it works".  (originally my samples were on floppy, these are on CD, so I have to extract the patches to floppies first to even be able to load them, and my friend wants his CD back!  The "normal" way to use it would be to have a SCSI add-on board for the keyboard and a special compatible CDROM drive, but I didn't spring the $800 for that back in 1992.)

Thanks!

---

### Post by notasquirrel on 2007-08-26
I'm also seeing a command 'cdrdao'.  Is this closer to what I want:

cdrdao read-cd --device 0,4,0 --buffers 64 --driver generic-mmc-raw --read-raw toc-file.toc

The context I found it in was making images of audio CDs, which don't have a filesystem.  (I don't have a readable filesystem per se, but it's also not an audio cd...)

Or do I do cat /dev/sr0 > file.iso?

this command:
isoinfo dev=/dev/sr0
gives "CD-ROM is NOT in ISO 9660 format"

---

### Post by steveneddy on 2007-08-26
Data on a CD or DVD is only ones and zero's.

Use K3B to burn a data cd.

---

### Post by notasquirrel on 2007-08-26
Thanks, looking that up now...

---

### Post by notasquirrel on 2007-08-26
K3b wants KDE and I'm in Gnome.  Is there an equivalent command-line method?

[edit] 
NM, Aptitude says "K3b is a frontend for cdrdao and cdrecord."

So that more or less answers my question...  looks like cdrdao is the command to use for making raw binary images without any regard for disk content.

---

### Post by steveneddy on 2007-08-26
K3b will install with Gnome, although it will install some of the KDE libraries for you that it needs to work well.

Go ahead, try it. You may like it. 

I find that is a very intuitive CD/DVD burning suite, and I'm on Gnome, too.

---

### Post by notasquirrel on 2007-08-26
OK cool, I'll try it later then.  I already have Amarok installed which installed a bunch of KDE libs, so when K3b wanted more KDE stuff I thought it must be going for the whole thing.  (Sounds like it just needed something Amarok didn't.)

For anyone else finding the thread in a search:

I ran across the 'readcd' package (or rather 'readom'?  'man readcd' points to a manpage for readom.)  A guide I eventually found pointed to it as a solution for reading out raw 1:1 images in a way that allows error correcting for slightly scratched sectors.  According to that guide 'cdrdao' is for audio pretty much, and the other way for data cds would be to use dd.  (which doesn't do error checking)

I prefer the command line stuff because my main linux box is an mp3 jukebox on my stereo, with a small screen and obnoxious keyboard and mouse.  Also because I can make a little shell script to do a 1:1 cd duplication.

readom is already getting several uncorrectable sectors as I've typed this, even at 2x, so I may have to give K3b a run and see if it fares better.  This CD has probably been hanging around my friend's studio for over 15 years!

---

