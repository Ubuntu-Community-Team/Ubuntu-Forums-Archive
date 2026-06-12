---
title: "Boot Sequence dell inspirion 15 3521"
date: 2014-01-18
forum: General Help
---

### Post by ohanoch on 2014-01-18
Hello,
I am sure I'm not the only one with this problem but i couldn't find a post answering this question directly:
After installing Ubuntu 12.04 in duel boot with windows 8 I know want to change my boot sequence to automatically boot from Ubuntu. In the Bios there is now Boot options other than enabling and disabling Legacy and UEFI (I need both, Ubuntu is Legacy Windows is UEFI).
Where is the good old fashion boot sequence menu? How can I do this.

I am new to Linux all together so if I need to do something complicated I would very appreciate step by step instructions.

Thanks in advance for any help anybody can provide!

---

### Post by oldfred on 2014-01-18
Best if both are UEFI. 
If Ubuntu is legacy and Windows UEFI, you can only boot from UEFI/BIOS menu or one time boot key. 
UEFI and BIOS are not really compatible, so once you start booting in one mode you cannot change, or then grub menu will not work.

If Ubuntu is in legacy/BIOS mode you can convert to UEFI mode with Boot-Repair. But it may be better to install 13.10 or wait for 12.04.4 in a few weeks.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

---

