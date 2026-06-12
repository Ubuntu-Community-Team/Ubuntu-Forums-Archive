---
title: "USB flash drive full; reports size incorrectly"
date: 2006-11-15
forum: General Help
---

### Post by fisherman783 on 2006-11-15
I have a card reader for my SD cards that, in Windows, got them to be treated just like any old flash drive would with no problems.

In Ubuntu, when I insert a card into the reader, it mounts automatically without a hitch.  Appears on the desktop and in the media devices listing, can read and write files, everything no problem.  The "only" problem is that the card size is read incorrectly.  I currently have a 512MB card in that Ubuntu thinks has about a 425MB capacity.

In some previous net searches (which I can't seem to re-locate now...), I found a couple forum posts out there from people (mostly on other distros) who had the same problem.  It seems that Linux has a habit of thinking that a flash drive's capacity is equal to however much space on it happens to be used when you insert it, resulting in a chronic inability to write files to the drive until you delete something.  Some reported to have worked around the issue by inserting their flash drives into a computer (like an XP box) that handled them correctly, filling the drives up with junk files, giving them back to the Linux box - which, upon mount, fools it into handling the size correctly - then deleting the junk files and replacing them with whatever you wanted to put on the flash drive in the first place.

I didn't find any reports of a "real" fix out there, though.  This is a horribly laborious workaround, and I'm inclined to think that there's got to be /some/ way to make it work right.  Can anyone offer any insight?

---

### Post by sjnovick on 2006-11-15
In Nautilus, click on "view hidden files".  This will reveal your .Trash.yourname (where yourname is your log-in name).  In Ubuntu, when you delete files from a USB drive, the files go not to your desktop trash bin, but to the USB drive trash bin.

If this is the case for you, simply empty the USB drive's trash bin to regain your "lost" MBs.

---

### Post by fisherman783 on 2006-11-15
In this instance I had, to my chagrin, forgotten to empty the trash, but it doesn't fix the original problem I was trying to describe.  Having emptied the .trash-username directory, I now have a 512MB card that is reporting a capacity of 488MB.

Perhaps I should have mentioned that this happens even the first time that a card/drive is used with Ubuntu, before files would have been placed in the .trash directory.

---

### Post by strabes on 2006-11-15
In nautilus if you go to edit, preferences. The last option on that page lets you include the option to delete files completely instead of moving them to trash folders. This is useful for flash drives, ipods and things of that sort. Hope this helps.

---

### Post by Hancoque on 2006-11-21
The size reporting is correct. Do the math: 512,000,000 bytes / 1024 / 1024 = 488.28125 MiB. The catch here is that storage capacities generally don't use the binary units but the "real world" decimal units where "kilo" means that something is multiplied by 1000 and not 1024. And companies don't even lie to you with that. They just use your lack of knowledge to their advantage, because bigger numbers sell better. In fact the proper binary unit is KiB and not KB (MiB vs. MB, GiB vs. GB respectively). The main reason why so few people are aware of this is because even OS makers don't use correct units. They use KB/MB/GB where they actually mean KiB/MiB/GiB.

---

### Post by fisherman783 on 2006-11-29
> **Hancoque said:**
> The size reporting is correct. Do the math: 512,000,000 bytes / 1024 / 1024 = 488.28125 MiB. The catch here is that storage capacities generally don't use the binary units but the "real world" decimal units where "kilo" means that something is multiplied by 1000 and not 1024. And companies don't even lie to you with that. They just use your lack of knowledge to their advantage, because bigger numbers sell better. In fact the proper binary unit is KiB and not KB (MiB vs. MB, GiB vs. GB respectively). The main reason why so few people are aware of this is because even OS makers don't use correct units. They use KB/MB/GB where they actually mean KiB/MiB/GiB.

Yep... that would do it.  Thanks for pointing it out.  I hope this helps other people to have this all in one place now.

---

