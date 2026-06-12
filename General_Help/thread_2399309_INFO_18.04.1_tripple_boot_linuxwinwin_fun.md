---
title: "INFO: 18.04.1 tripple boot linux/win/win fun"
date: 2018-08-23
forum: General Help
---

### Post by Kris_M on 2018-08-23
Was running win7.
Installed win10 alongside so then it double boots. Or actually it boots to the win10 bootloader which offers you both!
Cool.

Yesterday installed 18.04.1 alongside them.
Grub offers me all 3.
However.
Choosing win7 doesn't work (since the win10 bootloader has taken it over).

To get to win7, at GRUB:choose win10 - that boots to the win10 bootloader which offers you 7 and 10, Choose win7. system reboots to GRUB heehee _choose win10 again_ and it will now boot direct into win7.

However, the next time you reboot to GRUB and choose win10, it will boot to the win10 bootloader and offer you both.

Took me a few minutes to figure this out. I understand it but think it's a giggle. :)

That's why it is so important for me to use a backup that preserves all of these pointers or I risk losing everything - just running Rescatux and re-installing GRUB won't do it for anything other than Ubuntu and maybe win10, but quite possibly not.

---

### Post by oldfred on 2018-08-24
You can reconfigure to directly boot both Windows from grub. 
You just need Windows boot files in both systems. 
Windows uses Boot flag to know which partition to boot from which now is usually a separate Boot partition. Last install of Windows then overwrites the boot files and takes over boot by updating BCD.

But grub just looks for boot files.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

You should be able to just move boot flag to Windows 7 " c: drive" and run repairs using Windows 7 repair disk. Then move boot flag to Windows 10 and run repairs using Windows 10 repair disk. Repairs will only work if both installs are primary partitions. But you may be able to manually copy files & edit BCD.

      
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Kris_M on 2018-08-24
> **oldfred said:**
> You can reconfigure to directly boot both Windows from grub. 
You just need Windows boot files in both systems. 
Windows uses Boot flag to know which partition to boot from which now is usually a separate Boot partition. Last install of Windows then overwrites the boot files and takes over boot by updating BCD.

But grub just looks for boot files.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

You should be able to just move boot flag to Windows 7 " c: drive" and run repairs using Windows 7 repair disk. Then move boot flag to Windows 10 and run repairs using Windows 10 repair disk. Repairs will only work if both installs are primary partitions. But you may be able to manually copy files & edit BCD.

      
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)


Thanks for your time.

a) I am hoping to not use either win very much, so:
b) if it works, don't fix it! - This seems to work the way MS intended. I will boot to them once a month at the beginning of the month - before update Tuesdaty - and update them to keep them current.  I thought I was away from them (win) before when I was on 16 and 17, but I was on a box then and screwed up my video cards and the kernel got so confused and wouldn't boot (I'm sure if you were here you could have bailed me out, but I have no knowledge - a babe... so back to win for a while. But couldn't resist 18.04.1 LTS, and I'm on just a Laptop now, so no video drivers at all, so much simpler for me.  The downsize feels good, I guess my next step will be to put my old games back up. Then we'll see. Actually (from the other thread) my next step will be to pick up a 2T hd and set up work and fstab on that and copy it over, and THEN go the games. It's a toy! Always a toy!!!

Thanks again!

Another update just came in - one thing I love about Ubuntu - but i saw GRUB go by so better install the customizer in case I have to. :)

---

