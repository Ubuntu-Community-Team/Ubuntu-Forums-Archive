---
title: "grub error: symbol 'grub_term_highlight_color' not found"
date: 2014-05-17
forum: General Help
---

### Post by bas5 on 2014-05-17
When starting up, grub loads normally. When I enter the Windows entry of Grub, I get into grub rescue with the _error: grub symbol 'grub_term_highlight_color' not found_.

I had windows 7 installed together with ubuntu 12.04LTS on two different partitions of the same harddisk. I did updates in ubuntu, while Windows was in hibernation (I suspect this was the problem).
Then windows wouldn't boot anymore, and I tried upgrading to 12.10. Then Grub didnt load at all and all I had was grub rescue.
Then I installed ubuntu 9.10 from a disc I had laying around. Then installed 14.04.

Now, _Ubuntu works fine, but I want to get windows back working_.

I think I need something from here:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
I already tried dpkg-reconfigure grub-pc without success.

Or should I try to reinstall the windows mbr like this:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

Can someone help me out? I would be happy if I won't have to do a clean windows install

I dont know if it is relevant, but I also have a Wubi installation in the windows partition

Thanks in advance

---

### Post by oldfred on 2014-05-18
If Windows is still there after all the re-installs, and was hibernated, you may have to install the Windows boot loader to boot into Windows and turn off hibernation. If you did any auto installs it would not have seen Windows and may have just reformatted entire drive. If you always used something Else you should be ok.

Grub will only boot working Windows and if Windows is hibernated, the os-prober cannot mount it to see if it has boot files to add to grub menu.

May be best to see details.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You can use Boot-Repair in advanced mode to install a Windows boot loader or a grub boot loader. But it wants to see the system to know what boot loader and if Windows is hibernated not sure it will work to reinstall a Windows boot loader in that case.

---

### Post by bas5 on 2014-05-19
Thank you for your help.

Boot-repair did not work, but I got it back working by using Testdisk from the terminal of a live-cd. I had to repair the bootsector by loading a bootsector backup.

Now I can only use windows, but not Ubuntu yet, but I am not in a hurry to repair Ubuntu, because I rarely use it(although it works super). I can make it by just reinstalling Grub I guess

Thanks again!

---

