---
title: "Grub Rescue"
date: 2014-04-30
forum: General Help
---

### Post by Nabz23 on 2014-04-30
Hi guys,

I've ran into an issue. I downloaded ubuntu 14.01LTS and then I mounted the image on power iso, and then I ran the image. Once I ran the image it had an option for it to download a boot runner so that once I restart my computer there would be a boot screen that would direct me into installing ubuntu. Well I restarted my laptop and it went to the black green with error: unknown file system, and then grub rescue> below it. I looked into this and downloaded YUMI and used it to put the super grub disk onto my USB. I restarted my laptop and booted with my usb and it opened with YUMI, super grub disk 1.98. I chose windows vista bootmgr or btmgr (sorry cant remember exactly). And then it gave me the option to open Ubuntu or Windows 7. When I clicked Ubuntu it was on the boot screen for quite some time and then a message came up saying:

```
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system
```

So I had to power off my laptop then turn it back on and then I booted with USB ran YUMI and this time chose Windows 7, it opened up perfectly. 

BUT, Here is the problem, If I remove the USB and I restart my laptop, it just goes to the grub rescue> , rescue screen.

Is there any way to boot Windows 7 without this problem??

Thanks guys!

---

### Post by oldfred on 2014-04-30
Not sure how you got grub boot loader into MBR without the rest of grub. If you had a full install then grub would load a menu to boot either Ubuntu or Windows.

But you need to reinstall a Windows boot loader to the MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Or use your Windows repair CD or flash drive.

 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by Nabz23 on 2014-05-01
Thanks, 

Now I have a new problem with the same problem pending. When the screen came to choose Ubuntu or Windows 7 i choose pressed F8 to go to advance boot settings then I decided to try out the option to open windows from last working configuration so I did that but the wifi won't turn on anymore. Everytime I restart my laptop now there is no wifi.

I will try to fix the boot loader problem first using the windows disk option. Any clue on this wifi issue?

[B]
Edit:
[/B]The link to download windows repair disk for win7 64bit, files removed. [from the help option one you gave me the bootloader one]

---

### Post by oldfred on 2014-05-01
No idea on wifi.

The one link that used to be a free download for Windows repair ISO, now charges. I think any other links are gone. Best to make your own when Windows is working.

---

### Post by Nabz23 on 2014-05-02
Thank you so much, I used the window repair disc and then the command prompt and it worked. I also installed Ubuntu properly. I just have a quick question, when you click the power button on the top right and it and click About This Computer, it gives info, and then it says Disk 9.4GB, does that mean i got 9.4 GB of things i can download/save on this disk? I know it's a newbie question, just wondering I was confusing myself with something else. 


Thank you again!

---

### Post by oldfred on 2014-05-02
I assume that is the size you made / (root). It uses 4 or 5GB and 9.4 is on the small end of what I suggest, so you may need to houseclean. I use 11GB with lots of apps installed, but have all data including some of the normally hidden files & folders in /home in my data partition(s).

This shows mounted partitions size & use. From terminal:

df -h

---

