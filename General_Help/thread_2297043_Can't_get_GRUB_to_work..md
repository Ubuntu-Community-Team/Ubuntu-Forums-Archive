---
title: "Can't get GRUB to work."
date: 2015-09-30
forum: General Help
---

### Post by zacharygillenwater on 2015-09-30
There's kind of a long story here, but basically GRUB goes into rescue mode now instead of actually working.

So a few months ago I installed Arch Linux as a dual-boot with my Windows 8 installation. With that, GRUB was installed and so my computer would boot into that and it worked and everything was good. Then, about two days ago, I was going to install Ubuntu MATE over that Arch Linux partition, but I decided to upgrade to Windows 10 beforehand to avoid windows overwriting it or something. But after I installed 10, I got the whole GRUB rescue mode thing. I figured that maybe if I installed Ubuntu MATE anyway, it might reinstall GRUB and work everything out. It didn't. So I looked up the problem, and tried boot-repair, which didn't work, and I tried installing it in the terminal (I think with grub-install), and that didn't work either. I realized that there was an extended partition on my hard-drive (probably left over from my Arch install), so I deleted that and used boot-repair again, which, again, didn't work. I'm using my Ubuntu MATE CD to do all this, if that matters at all.

I'd really like to get GRUB reinstalled and get back to using my PC so any help is appreciated!

---

### Post by yancek on 2015-09-30
If you used boot repair, it has an option to Create BootInfo Summary.  It would be useful if you could post that here so someone could review it and give you some suggestions.

---

### Post by zacharygillenwater on 2015-09-30
Sure thing! Here's the paste.ubuntu.com URL it gave me:

[http://paste.ubuntu.com/12628137/plain/](http://paste.ubuntu.com/12628137/plain/)

([http://paste.ubuntu.com/12628137/](http://paste.ubuntu.com/12628137/) since the plain version doesn't work now)

---

### Post by oldfred on 2015-10-01
It looks like you have grub, but no Linux for it to boot with. 

You may be able to use Boot-Repair's advanced mode to choose Windows and choose sdb drive for Window like boot loader. You will need boot flag first on sdb1.

And for Windows to boot you need a Windows boot loader in sdb and boot flag on sdb1. Or using your Windows repair flash drive set active on whatever Windows calls your sdb1 bootable partition. And fixMBR for sdb. You have to first set BIOS to default boot to Windows drive to correctly repair any drive other than sda (normal BIOS default) using Windows tools. Or change drive to first drive.

---

### Post by zacharygillenwater on 2015-10-01
If I installed Ubuntu MATE onto that partition, would it work? I have a Windows 10 disc I can use to repair it, though.

---

### Post by yancek on 2015-10-01
> If I installed Ubuntu MATE onto that partition, would it work?

Which partition.  All you have on both drives are windows (ntfs) partitions and you can't run any Linux system from it.  You would need to shrink one of the windows partitions on one of the drives to create unallocated space on which to install Ubuntu.  You should do this from the windows Disk Management software.  You should then be able to use either the Install Alongside method or the manual method referred to as "Something Else" in Ubuntu.  I've not used the Install Alongside method but from what I have read, control over what happens during the install is pretty limited.

---

### Post by oldfred on 2015-10-01
With Mulitple drives I really only recommend the Something Else install option. All auto install options install grub2's boot loader to sda. You want grub installed to the same drive as you install into. 
I also prefer with mulitple drives to have Windows on one drive & Linux on another drive, but that depends on how you want your data organized.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
      [/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

    [URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

---

### Post by zacharygillenwater on 2015-10-01
> **yancek said:**
> Which partition.  All you have on both drives are windows (ntfs) partitions and you can't run any Linux system from it.


I actually have an unallocated partition that used to have Arch on it.

I'm going to try installing Ubuntu onto that partition, I don't know how it could hurt.

---

