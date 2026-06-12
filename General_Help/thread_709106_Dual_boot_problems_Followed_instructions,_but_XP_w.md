---
title: "Dual boot problems: Followed instructions, but XP won't boot"
date: 2008-02-27
forum: General Help
---

### Post by ZimbuTheMonkey on 2008-02-27
Hey guys. Here are the steps I followed to dual-boot Linux Mint on my machine:

1. Freed up space in Windows. 
2. Defragged twice to ensure all data was at the beginning.
3. Selected recommended/optimal settings in the Linux install procedure.

Now I get to the GRUB loader selection page and can boot linux just fine. But when I select Windows XP in the list, I get the following error:

Root (hd 0,0)
Filesystem Type Unknown
Partition type 0x7
SaveDefault
Makeactive
Chainloader+1

It stays on that screen and I am forced to reboot.

I searched google for the key words in there and came across a thread detailing the same problem, but for Windows NT. The poster discovered that changing the disk type to "LBA" in BIOS fixed the issue. I fooled around in BIOS but found no such setting, is it referred to differently sometimes? 

Is this a common problem? Where did I go wrong? 

Any help is appreciated. Thanks in advance. I'll mess around in Ubuntu in the mean time. :p

EDIT: Ok, I fixed it. I changed the "Acess mode" setting in BIOS from "auto" to "large". I have no clue what that does exactly, but windows loaded just fine. It gave me a "new hardware found" popup which I thought was a bit odd. My problem is solved, but I remain confused, someone help me out.

---

### Post by Forrest Gumpp on 2008-02-27
I don't know that I can shed very much light upon what you should have been looking for in your BIOS, but I think there may be a feature called 'enable large block addressing', or 'enable LBA'.

It may be in a menu you get to from something near where you switch on or off your HDDs in your BIOS.  It probably is not on show during your top-level perusal of the BIOS options.

Hope this helps.

---

