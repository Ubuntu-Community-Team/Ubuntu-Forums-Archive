---
title: "mount: /dev/ is not a block device"
date: 2007-02-11
forum: General Help
---

### Post by HinrikW on 2007-02-11
I've got a quite huge problem right here - I installed Ubuntu half an hour ago without any preparing at all, which is quite dumb I have to admit but I need a solution for my problem. I'm an absolute noob so please describe you answers detailed. 

I use Ubuntu or I want to use Ubuntu simultaneusly with Windows. So I installed it and needed to make a participation, well I did so and now I've got a huge Problem - Windows does no longer recognize the participation on which I installed Ubuntu and Ubuntu can't access the participation. 

It just says "mount: /dev/ is not a block device" - which doesn't help me at all.

Please help me as fast as you can, cause I'm missing those 30GB:(

---

### Post by davidvasta on 2007-02-11
Sounds like you wanted to keep and Install of Windows you have had running on a PC and have a Linux or Ubuntu partition so that you can run one or the other and things have gone wrong.

I have a few Questions:

1.Was Windows already on the PC before you installed Ubuntu?

2. When you installed Ubuntu did you have open space on your hard drive to allocate to a Linux partition or did you use the entire drive? You may have to think about this one.

There is always a word of caution if you going to use or install on a current working PC. You really have to think about what is going on and know that you could loose it all without knowing you just lost it all.

If you have a Windows Install CD you might want to boot from it and try to reinstall Windows or repair the install. Windows my in fact still be there but the MBR (Master Boot Record) may be damaged or just wrong and may need to be rewritten. 

The MBR is what Windows uses to boot from and you can edit it but in 20 years of being a geek I have never tried it so you are on your own there. You can in fact repair Windows with a CD and it will rewrite the MBR for you.

You may loose your Linux partition.

Here is the order in which I always help people upgrade:

1.Back Up all Data from Windows
2. Inform User they may loose all that data you just backed up.
3. Get user to nod head that t hey understand that.
4. Use Partition Magic or some type of partition tool to resize enough room to install Linux.
5. Insert Linux Install CD.
6. Use the available space to install linux on and do not touch the Windows partitions
7. Use LILO or GRUB to manage the boot process.
8. Linux should see the Windows partition and create and entry in the LILO or GRUB config files for you.
9. Reboot and see what GRUB or LILO says about booting. 
10. Test both Linux and Windows to make sure they are still there
11. Hold onto the Backups

-David

---

### Post by HinrikW on 2007-02-12
I participated a partly used device and the part with the windows data I can still usw in Windows (which is stil running) but the part on which I installed Ubuntu I can't use at all - not with Ubuntu and not with WIndows. 

The Device is named Floppy Disk 1, which is crap, cause it is a normal device, and if I click on "Datenträger Einbinden" (I'm from germany) the google translator says its called merge device in english but I'm not too sure about that. The computer says "mount: /dev/ is not a block device"

The same **** if I just try to use the device

Windows doesn't recognize the device at all, but recognizes at least the other part of the newly created participation

Hope that does help a bit more . Thanks for you really nice  and detailed answer, but I think my description was just a bit too bad

---

