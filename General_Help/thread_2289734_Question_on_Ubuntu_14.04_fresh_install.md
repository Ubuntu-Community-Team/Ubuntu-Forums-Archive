---
title: "Question on Ubuntu 14.04 fresh install"
date: 2015-08-06
forum: General Help
---

### Post by sports fan Matt on 2015-08-06
What is the easiest way to dual boot a fresh Ubuntu 14.04 install that had Windows 7 on it before upgrading it to Windows 10 if the live CD says multiple operating systems are installed but there is no option to upgrade the Windows7/10 part (wanted to divide it in half). If I resize the partition using Disk management in Windows, would this effect the fact that at least from what I know I have Windows 10 and the "recovery" option for Windows 7 because I have not gotten rid of the reserved partition?

---

### Post by oldfred on 2015-08-06
You have been around for a bit and should at least understand that Ubuntu typically installs to / (root) & swap.
Much better to use Something Else to install if you know which partition you want to use for Ubuntu or have partitioned in advance.
I normally use gparted to create partition(s) in advance. But you still use Something Else and click on change button to choose format, mount like / (root) for each partition. 

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

---

### Post by gordintoronto on 2015-08-07
Before you do anything, make sure you have a full backup.  (Eg. using Macrium Free to an external drive.)

Then have a look at the existing partitions. If this is an MBR disk (not GPT) and there are four primary partitions, you need to do some stickhandling before you can install Linux. What brand and model of computer? How old? What partitions?

---

