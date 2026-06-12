---
title: "Glary Utilities"
date: 2016-03-27
forum: General Help
---

### Post by Del_80 on 2016-03-27
Hi.....Anyone know if Glary Utilities will work with Ubuntu ?......or is there a good free alternative ?.......I use Glary on my Windows machines and find it very good........Del.

---

### Post by grahammechanical on 2016-03-27
Windows utilities and applications cannot run on Linux. They are not written to run on Linux. Unlike Windows Linux does not have a registry. So, we do not need a registry clean-up or repair tool.

The way the Linux has been crafted does away with many of the problems that Windows user have. Perhaps you can list which to the utilities that come with Glary that you would like to be available in Linux. You may find that they are covered by existing Linux utilities or are unnecessary in Linux. I have given you one example. Another example is, defragmentation.

[http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/](http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/)

The blog mentions briefly the fsck command. File system check command we can run that in a terminal or from the boot menu Advanced options for Ubuntu sub-menu. We select a recovery mode kernel to load and at the recovery menu we select fsck - check all file systems. We also have options to 

clean - try to create free space. It will run 2 commands - clean & autoremove
dpkg - repair broken packages

The Ubuntu install disk will give us options to check disc for defects and test memory. At the first purple screen we press Enter. Then select a language and there are the options. After running these tests we can select to boot from the first hard disk.

Regards.

---

### Post by Del_80 on 2016-03-27
O.k......Thanks for that......is it also correct that I don't need an anti-virus program on a Linux system ?.......Del.

---

### Post by oldos2er on 2016-03-27
Generally, no, unless you're running a server or sharing email with Windows users. Best to read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") and decide for yourself.

---

### Post by Del_80 on 2016-03-27
> **oldos2er said:**
> Generally, no, unless you're running a server or sharing email with Windows users. Best to read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") and decide for yourself.   O.k Thanks for that.

---

### Post by speartip on 2016-03-27
The Linux file system is totally different to Windows and does not decay over time to the extent windows does.
If you want to keep your system clean of excess crud, my suggestion would be to install ubuntu tweak from here:
[https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download)
The 1st .deb file is what you need. Once installed use the Janitor to keep your system clean. 
Generally nothing else is needed.

---

