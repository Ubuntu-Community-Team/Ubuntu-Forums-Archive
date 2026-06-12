---
title: "Is it possible to boot multi Ubuntu with same version?"
date: 2016-04-07
forum: General Help
---

### Post by ender7 on 2016-04-07
Hi,
First of all sorry for this very basic question-answer thread but I could not found answer on the internet and try-learn would be very costly for me.

I now, I can boot different version of Ubuntu in the same machine. What I want to know is that can I boot two or more Ubuntu 15.10 in the same machine?

I will install one to SSD and one to HDD. My fear here is that grub may see them same and let me boot only one of them.

The reason for that I will use one for my work and one for my thesis. I want them to be separate. If one of them fall or needs to be fallen, the other one can survive.

---

### Post by sudodus on 2016-04-07
Yes this is possible.

You will be able to select version via the grub menu (or in some computers via a hotkey if one of the drives is connected via USB). Normally, the instance that you installed latest 'owns' the bootloader - but you can easily select the other one. I do this many times when I test the developing version of Ubuntu.

---

### Post by ender7 on 2016-04-07
Thank you very much for the answer. Now, I am in peace.
I hope this thread helps someone in the future ;)

---

### Post by oldfred on 2016-04-07
UEFI or BIOS.
I have done both and in both cases you want to partition in advance with gpt if UEFI or only Ubuntu. 
Windows has to have MBR partitioning to boot in BIOS mode.

And you need to use Something Else to install. Then you choose which partition to install into and which drive to install grub into, which works in BIOS boot mode.
But with UEFI grub always installs to the ESP - efi system partition on sda. I quickly learned to back that up before my other installs on sdb or even another install on  sda, unless I wanted new install to be default boot.  I then copied files & folders from ESP on sda to the ESP I had previously created on sdb.

In either case grub2's os-prober in last install should find all installs and add them to grub menu as boot options.

You probably also want to use smaller / (root) or system partition and have a larger shared data partition. Then your data can be easily shared between installs. I do not use a separate /home as without data it is tiny, and only copy a few configuration files from one to the other. I usually use a script to edit & reconfigure some basic settings in every install. I export list of installed applications & use that to reinstall. Somewhat a test that my standard backup procedure works. 

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

