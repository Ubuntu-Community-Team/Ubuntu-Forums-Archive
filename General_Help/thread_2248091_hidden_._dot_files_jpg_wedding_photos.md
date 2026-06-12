---
title: "hidden . dot files jpg wedding photos"
date: 2014-10-12
forum: General Help
---

### Post by don-kozm0 on 2014-10-12
[COLOR=#333333]I have an extremly delicate problem. The photographer that recently took my wedding photos uses a Mac. I gave him an external HDD which he then formatted to FAT32 before copying over all the photos he took at our wedding. Got the HDD home (I use Ubuntu 14.04), and alle the photos were readable from the external HDD. No problem I thought. [/COLOR]

[COLOR=#333333]I then copied all the photos to a NAS I have at home. Again, all the photos were readable in Ubuntu when reading them from the NAS. I then reformatted the external HDD to NTFS (my wife uses a Windows pc) and copied all the photos to the external HDD. When mounting the external HDD on my wifes Windows pc we noticed somehting strange I have never seen before. Nearly half, but not all of the pictures filename(these are ordinary jpg files) started with a .(dot) at first, and the filesize was just 4kb per file. The files were also shaded in color, indicating that they somehow were hidden. Any idea why this is, and is there anyway to fix this?[/COLOR]

---

### Post by TheFu on 2014-10-12
dot files probably are not the real JPG image files, especially if they are 4Kb. That is metadata about the JPG created by the photographer's image editing tool.

If all the files on the ext drive are .dot files, then I suspect someone used a "move" instead of using a "copy".
Before doing anything that risks highly important files, make a complete, 100%, backup of the storage. If it is really important, make 2 or 3 of those.

FAT32 - people still use that?

---

### Post by coffeecat on 2014-10-12
Support, not chat.

*Thread moved to **General Help**.*

> **TheFu said:**
> 
FAT32 - people still use that?

The photographer was using a Mac, and needed to copy the files to a medium readable by a Linux system. In the circumstances, with files of less than 4GB size, FAT32 is the most sane choice.

---

### Post by TheFu on 2014-10-12
Doesn't FAT32 have a recently self-imposed limit of 32G? FAT32 from 2002 didn't have that limitation. This was an external HDD ...  just read that Macs ignore the new size limitation of MS on FAT32 file systems. Good for them!

---

### Post by SeijiSensei on 2014-10-13
> **TheFu said:**
> FAT32 - people still use that?

Sure.  Every USB stick or similar device is formatted at the factory with FAT32 to insure compatibility with all major operating systems.

---

### Post by mcduck on 2014-10-13
> **TheFu said:**
> Doesn't FAT32 have a recently self-imposed limit of 32G? FAT32 from 2002 didn't have that limitation. This was an external HDD ...  just read that Macs ignore the new size limitation of MS on FAT32 file systems. Good for them!

It's not a limitation on the FAT32 itself, only thing Microsoft did was that they changed Windows so that it doesn't allow you to create FAt32 filesystems larger than 32GB. :D (Doing it on any other operating system works just fine, and of course Windows will happily use the large FAT32 filesystem.)

So, not a limitation of FAT32 but instead a limitation of recent Windows versions. ;)


What comes to the actual topic, I agree with TheFu, all the dotfiles are most likely either metadata or thumbnail files created by the software the photographer used to import pictures or edit the raw images. They only became visible when moved to Windows since Windows doesn't hide files if their name starts wth a dot like OSX and Linux do.

So, I'd recommend just checking how many actual photos there's supposed to be, and as long as you have that many normal, working JPG files then everything is fine (and you can safely delete all the dotfiles).

---

### Post by jamesisin on 2014-10-13
Yes, you will likely discover that for .xxxx.jpg there is a corresponding xxxx.jpg (or whatever the naming scheme is).

---

### Post by don-kozm0 on 2014-10-14
Found the solution to this one :)


[http://www.peachpit.com/articles/article.aspx?p=1762250&seqNum=5](http://www.peachpit.com/articles/article.aspx?p=1762250&seqNum=5)

[https://forums.adobe.com/thread/1178564?start=0&tstart=0](https://forums.adobe.com/thread/1178564?start=0&tstart=0)

[COLOR=#3E454C][FONT=Helvetica]http://en.wikipedia.org/wiki/Dot-file


Oh, and also, no pictures were lost :):)[/FONT][/COLOR]

---

