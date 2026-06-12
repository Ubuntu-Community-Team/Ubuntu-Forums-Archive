---
title: "Resizing Windows 7 Partition broke both Windows and Ubuntu"
date: 2018-07-06
forum: General Help
---

### Post by jonathan90 on 2018-07-06
I'm dual booting with Windows 7 and Ubuntu, and I tried shrinking my Windows partition (from the right). I used Minitool Partition Wizard to do so (I have an HDD). I ran a fragmentation program first and then shrank the Windows 7 partition, but now the Windows partition is corrupted and Ubuntu sends me into "emergency mode." [Here is the output of fdisk -l]("https://i.imgur.com/N9OTT3K.jpg") (/dev/sdb is my live boot usb) and [here is the output from Boot Repair]("http://paste.ubuntu.com/p/QKd7jmVW7p/"). When I run OS Prober, it only finds Windows 7 (loader) on /dev/sda1 and doesn't output anything for Ubuntu. I get that Windows won't boot since the partition is corrupted, but I didn't do anything to Ubuntu. Does anyone have any ideas?

---

### Post by oldfred on 2018-07-06
The errors are from Windows.
And you typically have to run chkdsk from Windows own repair console, or a Windows repair flash drive. You cannot run chkdsk from Ubuntu.
Often you have to run chkdsk multiple times as it does not fix all the issues with one pass. Run until no errors.

It looks like you have newer UEFI hardware, but both Windows & Ubuntu are in the now 35 year old BIOS/MBR configuration. Be sure to always  boot in BIOS mode.

---

### Post by jonathan90 on 2018-07-06
Thanks for the reply! Unfortunately, I cannot boot Windows at all. When I try to select it from GRUB, it just takes me back to the Dell startup sequence with F12 for boot options and F2 for setup. Do you know if Ubuntu has any software that can do the same thing as chkdsk on the Windows partition? Also, how do I tell if I'm booting in BIOS mode or not?

---

### Post by oldfred on 2018-07-06
Grub only boots working Windows.
Best to have Windows repair disk. The Linux tool for repairing NTFS, only turns on the chkdsk flag, so Windows will run chkdsk when booted.
You may be able to temporarily install a Windows BIOS boot loader to MBR, then using f8 get into its repair console. After Windows is fixed then reinstall grub.
Boot-Repair may let you install a Windows type boot loader to MBR.
There also are some third party Windows repair tools that may offer chkdsk.

This is one advantage of UEFI, in that you can boot both Ubuntu and Windows directly from UEFI boot menu. Where with BIOS only one boot loader can be in MBR.

---

### Post by jonathan90 on 2018-07-14
Is it possible to fix Windows without a repair disk? Right now, when I try to boot Windows from Grub, it just sends me back to the Dell start up screen where it gives me the option to press F2 for setup or F12 for boot options. I can't get to anything in Windows right now. Thanks for your help!

---

### Post by HermanAB on 2018-07-14
Hmm, playing with partitions is a very reliable way to break a system.

While you are at it, you should consider expanding the Linux partition over the whole disk and using a virtualizer (VMWare, Virtualbox, KVM) for Windows.

The advantage is that you can then run Windows in a Window and do everything you need to do at the same time.

---

### Post by oldfred on 2018-07-14
Do not know Windows issues.
Your MiniTool have any repair options?

---

### Post by C.S.Cameron on 2018-07-14
It's probably better to use Windows to shrink a Windows partition, Use Windows Disk Management, it's quite fast.

---

