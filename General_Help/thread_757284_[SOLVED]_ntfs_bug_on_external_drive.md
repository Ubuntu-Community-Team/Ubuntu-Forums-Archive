---
title: "[SOLVED] ntfs bug on external drive?"
date: 2008-04-16
forum: General Help
---

### Post by nowhere@cox.net on 2008-04-16
I am having troubles with my 500GB Seagate FreeAgentPro drive. When connecting it to Ubuntu Gutsy i386 install, it automounts in gnome no problem. After being connected a while, random folders will no longer show any contents. Unmounting and remounting from a nautilus window fixes the missing folder contents.

The drive is formated NTFS and I do not have this problem when connected to the same PC booted in WinXP for extended times. So, I suspect something flakey with ntfs-3g which I am assuming is installed by default in a Gutsy install. 

It's very consistent in that eventually some folder contents will become unavailable (ie blank when you read and error when you try to write to the folder).

Anyone have any ideas?

Thanks,
Eric

---

### Post by wdaniels on 2008-04-17
Not heard of that particular problem before. I think it'd be worth checking the NTFS for errors from [WinXP]("http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/kbtip.mspx") and also search the system log for clues in error messages there.

---

### Post by nowhere@cox.net on 2008-04-28
No errors reported in windows. I think I will try to RMA it with Seagate. 

Eric

---

### Post by nowhere@cox.net on 2008-05-20
I found a work around. The problem seems to be with the drives internal sleep function. I booted in windows, loaded the Seagate Drive Utility and disabled the drive's sleep function and I have not lost "connection" since. 

I suspect I should report this as a bug somewhere. Any suggestions where?

Thanks!

---

### Post by wdaniels on 2008-05-20
Thanks for updating the thread!  I had a little look myself and found that there is a potential solution using the kernel's allow_restart parameter (see [here]("http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent")).

The place to file bugs is [Launchpad]("http://www.launchpad.net") but it seems there is already a bug filed for this (#[193154]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/193154")). Seems like the problem is solved in Hardy.

---

### Post by nowhere@cox.net on 2008-05-22
Ah interesting! Thanks. My server is still on Gutsy. It has a bit older nvidia graphics card which the install had troubles with requiring manual intervention and has both PATA and SATA drives for which the installer incorrectly sets up grub requiring more manual intervention so I have not upgraded to Hardy on it yet.

My laptop is running hardy and I have not seen the problem on the external drive so I need to plug it back in to the server for a while to double check that disabling the sleep fixed the problem. Then I will do a fresh install of Hardy and check again with sleep enabled and report back...

---

