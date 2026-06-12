---
title: "How to revert Windows SDA1 when installing Ubuntu 14.04"
date: 2015-06-20
forum: General Help
---

### Post by desmondcheongzx on 2015-06-20
I installed Ubuntu on a USB flash drive so that I could keep my Dell untouched and run Ubuntu on it.

When installing Ubuntu, my Windows 8.1 partition was listed as /dev/sdb, so when i unknowingly changed the type of system for my Windows /dev/sda1 to an ext4 journaling file system. Before installing I noticed that the partition size was too large, so I quit the installation process. However my /dev/sda1 settings were not reverted and I'm unable to boot into Windows now. I can still boot into Ubuntu using my thumbdrive right now.

Here's a screenshot of my current partition info
[ATTACH=CONFIG]262752[/ATTACH]

How do I get the Windows partition back to its original state?

Please tell me if you need any debugging info, I'm not familiar with the standard procedure.

---

### Post by nlee2 on 2015-06-20
Usually I would use Advance Boot Options to do a Auto Repair of Windows when the efi boot partition is messed up. If you are comfortable with the process, try resetting your bios to default settings.

What is the result when you boot without thumbdrive?
What is the key combination to get Advance Boot Options for your Dell?
Do you have Windows install media?
Did you make a USB recovery disk?

---

### Post by desmondcheongzx on 2015-06-20
I just get this screen when I boot without thumbdrive
[ATTACH=CONFIG]262761[/ATTACH]

I can still get to my boot menu before this screen.

I have a windows install media, but no usb recovery disk.

---

### Post by nlee2 on 2015-06-20
Set bios to Boot from your install media
Press any key to boot from CD or DVD
*Windows Setup* dialog appears. Click Next to continue.
Click Repair your computer in the lower left corner
*Choose an option* screen then appears. Click Troubleshoot.
click Advanced options in *Troubleshoot* screen.
In the *Advanced Options* screen, click Automatic Repair or Startup Repair.
choose a target Windows 8.1 operating system by clicking on its button
If repairs were successful, your PC will restart automatically.

[https://www.winhelp.us/repair-your-computer-in-windows-8.html](https://www.winhelp.us/repair-your-computer-in-windows-8.html)

---

