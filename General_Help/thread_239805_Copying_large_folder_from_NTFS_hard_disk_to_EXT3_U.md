---
title: "Copying large folder from NTFS hard disk to EXT3 USB disk failing"
date: 2006-08-19
forum: General Help
---

### Post by Yossarian on 2006-08-19
Sorry if this is the wrong forum.

I'm trying to copy a few large folders from an NTFS partition on an internal hard disk to an EXT3 partition on a USB hard disk.

The folders are say 12 gigs.  After copying about one fifth of the files, it threw a message saying: 

```
Error "Read-only filesystem while copying File X"
Would you like to continue?
```

I tried unmounting and remounting the ext3 partition through the terminal (as Nautilus and the desktop are currently unresponsive).  This did not fix the problem.

Any ideas?  Sorry for the lack of setup info, I don't know what would be needed for troubleshooting.

Forgot to add: the message mentioned above is a dialog with three options: skip, retry, and cancel.  Skip and retry do nothing.

---

### Post by Yossarian on 2006-08-21
I thought I'd post my solution, even though I'd be very suprised if anyone else had the same problem.  Read on if you're amused by stupid technical problems.

I figured this was some sort of GNOME problem.  My Windows installation got pwned somehow in the 2 months or so since I used it, so I booted up Knoppix and used it to do some copying.  That worked just fine (I was sitting across the room watching it).

My computer is a little older, so it has its USB ports in the back.  My new, fancy monitor plugs into one of those and acts as a hub.  The hard disk is plugged into my monitor.

Being a believer in the old fashioned form of power management, I always turn my monitor off when I get up to go somewhere.  When I was doing this it was interupting the connection between my PC and messing up the transfer.  So that was the problem.

Oh, it is to laugh.

---

