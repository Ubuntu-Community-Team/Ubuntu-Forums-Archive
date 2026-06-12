---
title: "Can bad things jump from live usb to HDD?"
date: 2016-01-25
forum: General Help
---

### Post by t0p on 2016-01-25
I use live usbs of Ubuntu on a laptop with Windows 8.1 on HDD.  If I mounted the HDD while using the live usb, and in ubuntu downloaded a file which was harmless to ubuntu but mean to windows, could the nasty thing slide over onto the windows system by itself (ie when I haven't deliberately moved the file over)?  I haven't yet mounted the HDD while in live stick ubuntu (it means disabling the windows quick-start/restart/hibernation settings which I haven't yet bothered to do).  But it's something I've considered (so I can use, say, my music files on the HDD while live-ubuntu-using).

Anything I ought to know?  I'm already aware I shouldn't put onto windows anything from ubuntu without a good scanning first. But can things slither across without my deliberate intention?

---

### Post by The Cog on 2016-01-25
I don't think so. In order to copy itself to a location that you didn't copy it to yourself, it would have to be active in Linux. I would not regard such a file as harmless to Ubuntu even if it chose to avoid damaging Linux and only damage any mounted Windows systems. I think that in general, hijacking the Linux OS would be a good enough prize, and that going on to look for attached windows drives is not something most malware writers would bother with. Governments with a specific target in mind are a different issue though.

I have never heard of a hijack that compromises Linux and then infects mounted Windows drives, but it is possible in theory. It is also possible in theory that a Linux hijack might choose to mount any unmounted drives and then infect them.

It is also possible to download files that would infect Windows if opened in Windows but that are harmless to Linux because they lack any Linux exploit content (e.g. media files, MS-Office files with macros etc), but you seem to be aware of that already.

---

### Post by sudodus on 2016-01-25
+1 to The Cog's reply.

I would add that if you want to share [virus free] files between Windows and linux, you should have ***a separate data partition*** with the file system NTFS (for example with the label **data**). It is not a good idea to write from linux in the system partition of Windows C:, it is much safer with D: 'data'.

---

### Post by Christopher_Stayne on 2016-01-25
It is also much less likely to get a virus on Linux.  Windows viruses are not capable of infecting a Linux machine (AFAIK) and most exploits used to download malware to your system without your knowledge depend on exploits found in Windows itself or the software made for it.  Therefore drive by malware downloads are far less likely (however not 100% impossible.)  I would do as has been said and transfer things to a seperate data partition rather than the OS partition.

---

### Post by t0p on 2016-01-26
Thanks everyone.  Marked thread solved.

---

