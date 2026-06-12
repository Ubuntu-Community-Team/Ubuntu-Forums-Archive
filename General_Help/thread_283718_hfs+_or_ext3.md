---
title: "hfs+ or ext3?"
date: 2006-10-24
forum: General Help
---

### Post by ike on 2006-10-24
Hi all,

I'm running MacOSX alongside Ubuntu edgy on an shiny new mac mini. I have ordered an external USB hard drive (iomega minimax 500gb) fot it, but i'm not sure what filesystem to use on the new drive. :-k 

FAT32 is not an option since it doesn't support files larger than 4gb.

I suppose i should go for ext3 or hfs+, but is MacOSX better at reading/writing ext3 than Ubuntu is at reading/writing hfs+, or vice versa?

I have installed ExtFSManager for the mac, but i can't get it to mount my ext3 partition.. ](*,) Is there a better application for this?

---

### Post by catlett on 2006-10-24
The 2.6 kernel has support for hfs+ but it may not be enabled. If you like to dabble, you can enable hfs+ support in linux and then format your usb to hfs+. Here are a couple of links. One is a driver for hfs+ (which may not be needed with 2.6 but I am not sure so I gave the link to you)[http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/) the other is a Gentoo wiki about hfs+ support [http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)  ( Just in case you are new to the different forms of linux. Gentoo doesn't use sudo. If you get a permissions error or something like that, put sudo in front of the command and run it again.)

---

### Post by matthewstory on 2006-10-24
I have a similar setup on a mac mini . . . but i run Ubuntu inside OS X, using Parallels.  The speed of Ubuntu is nearly as fast, and if you do it this way you can set up the drive HFS+ and then make a samba share for it in OS X which you can share with Ubuntu, as per a howto i wrote here:

[http://macusers.zedzone.com/wiki/view_entry.php?wikiEntryId=4049](http://macusers.zedzone.com/wiki/view_entry.php?wikiEntryId=4049)

---

### Post by Sef on 2006-10-24
I would go with HFS+ since it was developed by Apple.

---

### Post by ike on 2006-10-25
But can i get write permissions on hfs+ with linux? I have mounted my main MacOSX partition but i get read-only persmission. (which means hfs+ support is included in the 2.6 kernel)

Ext3 seems like a more "stable" choice, but since i can't get the mounting to work in MacOSX it may be a stupid one too..

I would like to avoid parallels and stuff, i just want to dual-boot.

---

### Post by happysmileman on 2006-10-25
What files do you expect to have that take up 4GB...

---

### Post by ike on 2006-10-26
> **happysmileman said:**
> What files do you expect to have that take up 4GB...

DVD images.

Now I am able to:
* copy files to the usb drive
* delete files on the usb drive (even those created in MacOSX)

But I can not *change* files on the usb drive created in MacOSX.. :-k 

Does anybody know why?

---

### Post by medgno on 2006-10-26
Linux has issues writing to HFS+ drives with journaling enabled. The thing is, journaling is a really nice thing to have. But if you want to disable it, under OS X, go to Disk Utility and then turn journaling off for the drive.

---

### Post by Linuxnz on 2007-12-11
Ike did you get it to work ok?  I also bought one and set it up on my Gutsy system and it is not recognised.

I formatted it as a small FAT32 partition and a large NTFS partition and it did not work.  My other USB drive works fine like this.

When you use sysinfo when you plug it in you see the hub appear and then the MiniMax and then it dissapears out of the tree never to be seen again.

Any ideas on this?

TTFN - Linuxnz

---

### Post by ike on 2007-12-11
> **Linuxnz said:**
> Ike did you get it to work ok?  I also bought one and set it up on my Gutsy system and it is not recognised.


My solution was to buy a Linksys NSLU2 (aka the Slug), install debian on it, and share the drive on the network with samba. It works great :)

---

### Post by Linuxnz on 2007-12-12
Ike, thanks for that.  I already have a NAS box, my Xubuntu Compaq EVO (cheapie NAS) and wanted to connect the MiniMax directly to it, but it doesn't seem to be recognised when other plain USB drives are.

Thanks anyway for your ideas.

Linuxnz

---

