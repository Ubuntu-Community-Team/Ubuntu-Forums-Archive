---
title: "How to configure grub 2.02 to load Windows 8 system"
date: 2015-09-24
forum: General Help
---

### Post by fkervin on 2015-09-24
Hi All,

I had a computer using ubuntu system in one of the hard drives, and everything was ok. Now I've add a second hard drive that contains Windows 8.1 and worked ok separately (without ubuntu disk). the result when trying to use both disks is quite ugly and I'd like to fix it. I explain:

First times I tryed to boot both systems, they worked (by default Ubuntu and Windows using bios boot menu). But then I had at every boot of ubuntu the GNU GRUB 2.02 Window that waits 10 seconds before start ubuntu. 

I tryed to remove this 10 seconds wait menu by editing /etc/default/grub (I've modify values of GRUB_TIMEOUT and  GRUB_HIDDEN_TIMEOUT_QUIET, then save and do "sudo update-grub" and "sudo  update_grub2")

Now the problem is not only I still have always this 10 seconds grub window, but I've broke the Windows boot. When I try to enter Windows using disk boot menu in BIOS I have this message:

[B]error: no such device: xxxxx-xxxxxxxxxxx-xxxxxxxxxxx-xxxxxx-xxxx
Entering recue mode...
grub rescue>[/B]

At this moment I actually have an option on the grub 2.02 menu for boot windows,  called "Windows 8 (loader) (on /dev/sdc1). The problem is that it  doesn't work. System gives this message:[B]

[B]error: no such device: F0Dxxxxxxxxxxxxxx
error: hd2 cannot get C/H/S values.
error: hd2 cannot get C/H/S values.

Press any key to continue

[/B][/B]I guess that if I cant boot directly from windows disk, the boot of this system is really broken.

sdc1 is the first partition of the Windows disk, and F0Dxxxxxxxxxxxxxx is its UUID. How could I fix it so it can boot Windows?I clear that both systems use legacy BIOS boot, not GPT/UEFI, althought  I've a third disk only for storage purposes (not booteable) that uses a  GPT partition in NTFS.

So I think I must repair windows boot and make the option of windows appear and work in the grub 2.02 menu. Of course, I don't want windows boot to be broken again if I run "sudo update-grub" or "sudo update-grub2" in ubuntu.
I'd really thank any help with this

Regards

---

### Post by oldfred on 2015-09-24
Lets see some details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

