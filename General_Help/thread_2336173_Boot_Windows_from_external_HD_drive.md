---
title: "Boot Windows from external HD drive?"
date: 2016-09-05
forum: General Help
---

### Post by aeronutt on 2016-09-05
I have an HDD from a previous computer with a Windows 8 OEM install. 
I also have my daily use laptop with several Ubuntu loads (currently with no Windows OS, but it originally had the above OEM HDD/Windows8 disk).

Can I install that OEM HDD in a USB drive enclosure, and boot/use Windows from my laptop?

(Just for the record, I've tried Wine and Virtual Box, and both have problems with the Windows Software I need to run.)

---

### Post by TheFu on 2016-09-05
Nobody here can say what cannot be accomplished. Lots of things believed impossible sometimes are possible, with enough effort.

I can say that what you want is very difficult.  OEM Windows licenses are tied to the BIOS of the system they came on.

My best answer is to clone the Windows install onto a larger HDD that can be installed into the laptop, then install Ubuntu as a dual-boot onto that same disk and use external disks for any large data needs for either OS.  I've moved from a 320G to a 500G to a 750G 2.5" HDD in an old laptop over the years. This is a well-known way to go and works fairly easily.

---

### Post by aeronutt on 2016-09-05
Ahhh...yes, makes sense, thanks. Recommended clone software?
Or at some point, the effort & cost isn't worth it compared to buying a cheap-o stand alone Windoes box.

---

### Post by TheFu on 2016-09-05
I'd use dd, ddrescue, partimage, clonezilla, or any of the 50 others out there.  Just depends on whether an exact copy is what you want or not.  With MBR paritioning, any of these would be fine. 

With GPT, then you probably want to manually clone the partition table using sgdisk first (so the 2nd copy is placed at the end of the disk, not exactly in the same place as on the source disk).  Then use something like fsarchive to move the partitions over into the exact same order they were originally.

My Win7 machine isn't UEFI, so MBR is required with it still.

---

### Post by yancek on 2016-09-05
The windows installer is designed NOT to install to a usb drive for obvious reasons.  Since you already have windows on the drive, the simplest way to find out is to test it by putting it in an enclosure.  I'd also agree that you would have better luck finding an answer to this question by going to the support.microsoft site or a windows 8 forum.  If you don't already have an enclosure, you might check windows forums before going out an buying one.

---

