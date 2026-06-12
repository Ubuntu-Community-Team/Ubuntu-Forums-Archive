---
title: "Shopping for an External hard drive"
date: 2007-04-18
forum: General Help
---

### Post by mrmonday on 2007-04-18
Hi all.

I am looking for an external hard drive, which needs to be:

[LIST]
[*]Incredibly Reliable
[*]Reasonably cheap
[*]At least 100GB in capacity
[/LIST]

I am not bothered how it connects preferably Ethernet, if not USB2, but it needs to be compatible with linux windows and macs. I am OK with putting it together if you know a good reliable deal with an enclosure and separate hard drive. I have seen some reviews, but would like to know what the users think.

Thanks.

---

### Post by thephotoman on 2007-04-18
Well, for this, any old hard drive and external USB enclosure will do--though, as most enclosures I've seen are PATA driven, you'll probably need a PATA hard disk.  Once you've put it all together, boot in Linux and run gParted (or QtParted if you're in KDE), and format the hard drive as FAT32, which is the only way to go between Windows and anything else.

---

### Post by trishacupra on 2007-04-19
See [http://ubuntuforums.org/showthread.php?t=411723](http://ubuntuforums.org/showthread.php?t=411723) for a discussion about which format to use. I'm currently deciding this myself for an external hard drive, and I have come to think that Ext3 would be best, and use the software at [http://www.fs-driver.org/](http://www.fs-driver.org/) because I will dual-boot with Windows. BUT I'm not sure if Ext3 is compatible with Macs, as that's not an issue for me.

For my external hard drive, I just bought a Samsung 400GB hard drive from a computer market, and put it in an enclosure that I already own. It took me less than 2 minutes to put it together.

---

