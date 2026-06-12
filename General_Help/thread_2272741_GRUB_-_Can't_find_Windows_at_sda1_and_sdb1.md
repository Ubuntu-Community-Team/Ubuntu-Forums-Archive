---
title: "GRUB - Can't find Windows at sda1 and sdb1"
date: 2015-04-08
forum: General Help
---

### Post by Jamie_Choi on 2015-04-08
Hi,

I have installed Grub2 & Grub Customizer on my Ubuntu.
I'm not sure what I did, but, however, when I run ```
sudo update-grub
```, I can't find my Windows 7 at both sda1 and sdb1. (I know I can't boot Windows from Grub.)

However, how can I find those two Windows 7 back? (All files are still safely here.)

P.S. How can I boot Windows from Grub?

---

### Post by grahammechanical on 2015-04-08
The Grub boot menu is a composite of a few configuration files. One of which is written by a Grub Utility called os-prober. It is this utility that looks for other operating systems including other Linux OS. We can disable os-prober. Or more accurately  stop the os-prober configuration file from being executable. If we do that then the update-grub command will not be able to run os-prober script and will not find any other OS.

You have got to undo what you have done. Perhaps you did it with Grub Customizer and can now revert the action. I have not used Grub Customiser for a while, So, I cannot tell you how to do it. 

There are other ways to set a script to be executed like a program. But these ways are a bit complicated to explain and give the user the power to break the OS.

Regards.

---

### Post by oldfred on 2015-04-08
If you have two or more drives do not run any auto fix. It writes grub everywhere and you probably want Windows boot loader on one drive and grub on the other drive. You can use advanced options to do that.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Grub2's os-prober looks for certain Windows boot files that normally are in the one Boot partition that Windows has. That usually is a 100MB partition with the boot flag.

---

### Post by Jamie_Choi on 2015-04-09
Yes, oldfred, you're smart but it's too late. Already ran boot-repair :) It wrote grub on sda1 :) I fixed it using WinRE.

However, still can't boot Windows using Grub. Any solution?

---

### Post by oldfred on 2015-04-09
Does Windows boot when you directly boot the Windows drive from BIOS?

Are you leaving Windows hibernated?

Post link to Summary report from Boot-Repair, but if Windows works on its own not sure if it will show much.

---

