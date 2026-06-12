---
title: "Partition/File system questions"
date: 2007-04-14
forum: General Help
---

### Post by Zeikcied on 2007-04-14
I have a couple questions about partitions and/or file systems.  But first, the usual back story.

When I first made the switch from WinXP to Kubuntu in October, the switch was gradual.  And I wanted to keep my "shared" files on FAT32 partitions, so that Windows and Linux could both read and write (previously I had them on NTFS, since I was only using Windows).  Now I'm exclusively using Linux.  So, a few questions...

1. Is there any graphical program that can defragment FAT32 partitions?

2. Is there any utility that can possibly convert FAT32 to ext3 without data loss?

3. Is there an easy way, within KDE (or using another program), to figure out the size (as in used, free, total) of my Root partition?  Other than QtParted and using the Properties menu in Konqueror.

Thanks!

---

### Post by rmemm on 2007-04-14
Use the "df" command line command to list partitian sizes.

I myself don't know about your defrag  and conversion questions.  I've not heard of any.  People on linux don't often do many things with FAT except read it and sometimes write it as exchange media.  Maybe someone else knows.

Rob

---

### Post by x1a4 on 2007-04-14
Hi,

Since dos/windows is/are the only operating system(s) in the World with file systems that fragment the way they do, there really isn't much of a need for defragmenting software.  Guess you just have to boot to windows and defrag from there.

---

### Post by RealG187 on 2007-04-14
Is it safe and possible to defrag USB HDs in FAT32? Windoze corrupts my apps so I use Auslogics defragger. Could I wine this or would that be dangerous, shoud I leave defrag to Windows?


Also I cant save directly [save image as, or rip CD] to My USB HD in FAT32, I have to save/rip to home folder and then copy, is there a way I can directly put files in?


Also.........

...........


NTFS! I can read but not write, I probably shouls leave this alone for safety right? I have my other USB HD as a backup. My first one is FAT32 for compatibility w/ Linux, Windows 98.

And my other one optizmized for backup, NTFS compressed. I do my backing up in XP....

---

### Post by rmemm on 2007-04-14
Personally I'm really conservative -- I'd stick with windows apps to do things major to windows formats -- and defragging is pretty major.  I've never tried to defrag a usb key -- but I don't know why it wouldn't work -- though who knows.  As for wine -- I'd personally never trust that with this sort of thing unless I'd really really tested it -- then still I might not.

NTFS -- I'm not certain of status.  Thought I heard it made 1.0 status -- but don't know.  Historically write NTFS was always experimental -- don't know today.  Always better to be safe than sorry with file systems.

I don't know why you can't save directly to your USB key -- one would think this should be no problem.

Rob

---

### Post by Zeikcied on 2007-04-15
Ok.  Thanks for the responses so far.

Any idea on whether or not it is possible to convert from FAT32 to ext3 without any data loss?  Because, to "convert" from NTFS to FAT32, I had to copy files from the NTFS partition to a separate FAT32 partition, and I don't exactly have the patience to do that again (not to mention the lack of hard drive space for a new partition large enough to handle all those files).  I guess I could resize the old, create a new, then keep resizing both until I get everything copied, but that's probably a lot more risky.

---

### Post by rmemm on 2007-04-15
Regarding FAT to ext3.  As I said in a previous post -- I'm really conservative.  When it comes to file systems -- I don't like modifying, converting or moving them.  If I was doing it -- I'd backup up the whole partician to whatever media you use and then verify the backup before doing anything.  Then I'd do that again -- meaning have 2 backup copies.  I might even take a separate 3rd copy that's an exact disk image (which is different than a regular file by file backup) just in case.  Then I'd reformat the partician ext3 and restore from one of the backup sets.

The other thing I would say -- if it's not obvious -- if you don't backup hard drives in general then at some point your going to loose everything -- it's just a matter of time.  I say that because you need to have enough backup media anyway to maintain 2 or 3 backup copies at all times -- and this needs to be offline media -- an done copy at least needs to be off-site.

As far as lossless converting -- you usually loose some meta data going between file systems because different file systems keep different meta data.  Usually it does not matter so much because often this meta data is there but is not used anyway.  The other good thing is that ext3 has richer meta data than FAT anyway -- so your going in a good direction.

Tools to do direct converion -- I don't know of any but there may be some as I said before.  Just don't know myself and I'd be cautious even if I found something.

Rob

---

### Post by RealG187 on 2007-04-16
You can copy to another HD reformat and put back, or burn to DVD, but its painful, but when I wanted to convert FAT to FAT32 it was taking forever, it was just faster for me to reinstall Widnows 98....

Anyways, I hardly trust Windows, it messed up my USB hard drive and my MP3 player [flash drive, drag and drop songs]

---

### Post by lotacus on 2007-04-16
I believe NTFSTOOLS can do this, but I am not really sure.

---

