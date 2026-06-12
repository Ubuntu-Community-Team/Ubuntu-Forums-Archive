---
title: "Need help getting back to dual boot menu"
date: 2013-06-24
forum: General Help
---

### Post by bruce73 on 2013-06-24
I installed 13.04 on my Win 7 desktop. Windows didn't present a dual boot menu, so, with help from here, a grub boot menu was created. I had to restore an image of my C: drive this morning and now when I try to boot "unknown file system" comes up with a "grub rescue >" command line. What do I need to do in order to boot into Windows again?

---

### Post by Mark Phelps on 2013-06-24
Can you boot into anything?  It looks like neither Win7 nor Ubuntu work at this point.

If you can boot into Ubuntu, then you can try using Boot-repair:  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If you can not boot into Ubuntu, and not into Win7 either, then you should have taken the trouble BEFORE you did the dual-boot to make the free Win7 Repair CD.  Without a working Win7, you can't do that for free anymore.  Instead, you will have to go the link and purchase a Win7 repair CD ISO file, download it to a PC, and burn a CD of it:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that CD and run Startup Repair three times -- that's right, three times.

---

### Post by bruce73 on 2013-06-24
Well, ya know, I DID take the trouble to make the free Win7 Repair CD.  Thanks for the advice.

---

### Post by oldfred on 2013-06-24
That will get you to boot Windows directly, but then you cannot boot Ubuntu from Windows.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

