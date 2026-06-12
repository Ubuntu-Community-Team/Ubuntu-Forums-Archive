---
title: "Windows partition in Linux"
date: 2008-03-19
forum: General Help
---

### Post by spo0neybard on 2008-03-19
Is it possible to run a windows partition in linux in a window? I've searched everywhere,
but on google it says: Dual boot! Linux inside windows! VMware! But these are not precisely
what I am looking for. I was wondering if it was possible to run my windows partition inside linux
with as much functionality as dual booting except not to the extent of actually rebooting.
If anyone knows such of a program or way than please post it. Thanks.

---

### Post by freebeer on 2008-03-19
When I installed 7.10 I was able to read/write to the NTFS (Windows) partition right out of the box.  Is this what you're looking for?

---

### Post by uidb4056 on 2008-03-19
You can install VMWARE Workstation for Linux and you only have to boot Linux then you can install windows in wmware and run it in a window. But vmware is not free even not too much expensive.

Another posibility is Parallels ( [http://www.parallels.com/products/workstation](http://www.parallels.com/products/workstation) ), also not free. You can download both and test it for a limited time and then decide.

Another possibility if you plan to use the new Hardy Heron release 8.04 (currently on a version Alpha 6 and planned to be realeased for production at end of Aplril). This release have integrated virtualization tools that will let you to work in the way you are looking for. Anway I recomend you to test it when it's released for production, of course you can try now if you want at your risk ( [https://wiki.ubuntu.com/HardyHeron/Alpha6](https://wiki.ubuntu.com/HardyHeron/Alpha6) )

---

### Post by jocko on 2008-03-19
> **spo0neybard said:**
> Is it possible to run a windows partition in linux in a window? I've searched everywhere,
but on google it says: Dual boot! Linux inside windows! VMware! But these are not precisely
what I am looking for. I was wondering if it was possible to run my windows partition inside linux
with as much functionality as dual booting except not to the extent of actually rebooting.
If anyone knows such of a program or way than please post it. Thanks.

Virtualization is the closest you get. There are several free (=no cost) programs, e.g. virtualbox, vmware player and vmware server.
A drawback with virtualization is that it doesn't use the hardware directly, so it will not work as well as if you run the os "for real".
You can run an existing windows installation directly from the hard drive with vmware or virtualbox, but it requires that you set up a new hardware configuration for windows (and I don't know if this will violate your windows licence or not). [Here]("http://ubuntuforums.org/showthread.php?t=631671") you may find some helpful links.
Search the [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") or [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") sections for more help.

---

### Post by spo0neybard on 2008-03-19
Thanks for the quick replies. Virtualization won't cut it since I've used my Linux for working
(school stuff not much since I'm ten) and my windows partition for gaming. (Halo, DoW,
etc..) I've also tried other things such as  the latest update of WINE and Crossover 6.2,
but does just get me visual errors.  And yes there are ways to turn a hard drive into a VMware
thingy, (I've read about it somewhere) and run it like that, but I haven't done it since there
are so many reports of DirectX 9 not working anyway. I haven't tried Parrels because it had to
do something with I didn't have a Mac. With VMware workstation (which I've tried) also has 
DirectX 8 in my opinion (no offence) is for old games. I've also tried virtual box, but it won't
show up in my system tools folder thing. Read and Write NTFS. I'm not into that much of 
computing and I have no idea what that means. Sorry. uidb4056 that's the closest thing
 I've come into looking for, but unfortunately I would try the beta, but would not like to jeapordize
my system. I will look into the release of it though. Thanks again for the quick replies.

---

