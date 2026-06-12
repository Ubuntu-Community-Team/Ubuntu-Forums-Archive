---
title: "GRUB woes"
date: 2008-02-26
forum: General Help
---

### Post by dimothy10 on 2008-02-26
Dear all,

I having trouble with GRUB.  I have Windows XP installed on a SATA RAID 0 and installed Ubuntu on IDE drive (CMOS has it listed as Primary Slave).  Forgot to tell the installation program to write to the correct MBR so it has embedded itself on the IDE drive.  I now want to edit the menu.lst to allow me to select windows from the list.  

From what I have read this should be fairly simple but I must admit I am really struggling.  I added the following to the menu.lst:

title		Microsoft Windows XP
root		(sda,0)
makeactive
chainloader	+1

This addition provides me with an Error 23 When Parsing etc.  
The output from fdisk -l looks like this:
Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb07db07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3715    29840706    7  HPFS/NTFS
/dev/hdb2   *        3716        7143    27535410   83  Linux
/dev/hdb3            7144        7297     1237005    5  Extended
/dev/hdb5            7144        7297     1236973+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01dd01dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001f01ff

Disk /dev/sdb doesn't contain a valid partition table


From what I understand I might have missed out a map command but from reading other posts am unsure as to what this command achieves and the proper syntax to use it in my case.  Hope someone can help me.

Thanks in advance
Tim

---

### Post by danwood76 on 2008-02-26
It is (hd1,0) not sda.
Grub looks at the various disks in order they appear and assigns them a physical mapping to hd0, hd1 etc.

So change that line to:
```

root (hd1,0)

```
and you should be ok.

---

### Post by dimothy10 on 2008-02-26
followed the above suggestion and all looked good until it said NTLDR missing.  By changing the boot order in CMOS I am still able to get windows to boot which to me suggests that NTLDR is fine but that my GRUB settings are pointing to the wrong drive/partition? 

Has anyone got any further help they could extend my way?  

Thanks in advance

tim

---

### Post by danwood76 on 2008-02-26
If it says NTLDR is missing that means its choosing the right partition.
What you need to do is use the map command to make it think its the primary drive.

I will try to explain in a little more depth:

When you chainload the windows drive it thinks its HD0, when infact its HD1, it looks to HD0 for the NTLDR but it doesnt find it as obviously this is the ubuntu partition.

What you can do is add a couple of commands to swap the drives over so it is then the first drive.
so I think it will look like this after:
```

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

```

This will then set the first drive to be your windows one and boot from there which should solve the problem.

---

### Post by torgrot on 2008-02-26
```

title Microsoft Windows XP
root (hd1,0)
map(hd0,hd1)
map(hd1,hd0)
makeactive
chainloader +1

```

You need to map the drives, since Windows wants to believe with all its heart that it is the single most important thing in your computer.  It would never think of booting off of anything other than the very first hard drive.  It would never cheapen itself by booting off the secondary drive.:)

Rats you beat me to it.  But I like my explanation better.

torgrot

---

### Post by danwood76 on 2008-02-26
Hehe, your explanation gets to the heart of the microsoft way of thinking ;)
I like it better than mine too!

---

### Post by dimothy10 on 2008-02-27
Thanks for the help guys but i still am getting errors.  Using the following entry in GRUB as suggested by danwood76:

title		Microsoft Windows XP
map		(hd0,hd1)
map		(hd1,hd0)
rootnoverify 	(hd1,0)
makeactive
chainloader 	+1

I now get the following error:

Error 11:  Unrecognized Device String.

I assume this has something to do with my map commands perhaps?

Thanks again

Tim

---

### Post by danwood76 on 2008-02-27
You could try using just root instead of rootnoverify.
use torgrots suggestion.

I havent tried my idea out, it was just a thought.

---

### Post by dimothy10 on 2008-02-27
Ok, so I have fixed the Error 11 problem.  Think I had an amalgamation of both your suggestions for the menu.lst and it did not like them.  This has only led me back to the NTLDR problem.  

I know that my NTLDR is present on my Windows partition as I am writing this message from Windows (after changing the boot priority in CMOS).  I understand that once I get past the NTLDR problem I will have to edit my boot.ini to represent the changed CMOS boot order but at the moment I can't get as far as that.

Most of the suggestions online seem to state that I need to replace the NTLDR as it is missing or corrupt.  This I do not feel is the case here.  Could it perhaps have something to do with my RAID drivers?  Ubuntu refuses to mount my Windows SATA disk and states "Bad Magic...." as a reason and that I should look at dmraid for answers.  I have even checked the device.map file and that has hd1 listed as sda1 so I am pretty sure it is reading the correct drive upon transferring to Windows.

All in all I am pretty frustrated lol.  If it was just a Windows system I would automatically use the Recovery Console and replace the NTLDR file.  seeing as it is still present on the disk though I am a bit stumped.  Could the changing of the boot priority in CMOS be causing a mismatch in NTLDR?

Thanks again in advance, you guys have been most helpful so far and apologies if I am being a touch thick in the head.

Tim

---

### Post by danwood76 on 2008-02-27
The NTLDR isnt missing or corrupt it just goes back to what we said earlier.
When the windows bootloader loads up it looks on the first disk first partition for the NTLDR (NT Loader).
The one thing is changing the BIOS boot priority may mess up grubs drive allocation.

I have my ubuntu (and grub) booting off of a RAID0 array but as I have said I dont use Grub to do my boot menu.

You could as an easier option just install GAG ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)) I use it all the time to boot either vista or ubuntu (from RAID0) and its far easier to setup than grub is.
You just select the partitons you want to boot each OS and it does the rest, it also installs completely in the MBR so you dont need and hard disk space for it.
You will still have grub on your linux partition as it is needed to boot linux ;)

Another thing to get the RAID0 array (called fakeraid if you need to search) to load you need to install dmraid.
then run sudo dmraid -ay for it to find your raid drive.

---

### Post by dimothy10 on 2008-02-27
Thanks for all the help guys.  Changed the boot order back to what it was before ubuntu and used superGrub to force it install GRUB on the windows disk.  had to edit a few of the lines in menu.lst to mirror the changes but all seems to work ok now as far as booting is concerned.  thanks again

---

