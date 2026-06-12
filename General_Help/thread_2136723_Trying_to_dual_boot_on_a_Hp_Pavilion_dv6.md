---
title: "Trying to dual boot on a Hp Pavilion dv6"
date: 2013-04-18
forum: General Help
---

### Post by illmattic on 2013-04-18
I have a hp Pavilion dv6 and the processor is AMD A8-3510MX APU with Radeon(tm) HD graphics 1.80. I'm trying to dual boot Windows 7 and Ubuntu 12.10 together. I created the allocated space but when I put in the live-dvd and reboot windows comes up. 

Matt

---

### Post by oldfred on 2013-04-18
Is the issue that live installer does not boot?
Then I would double check that download is correct, you can verify with md5sum. And re-install with unetbootin.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


 Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by illmattic on 2013-04-18
I'm pretty confident it isn't the cd. I was able to configure the booting order so that the cd came first and I was able to load it up and see the screen but it just gets messed up. So I'm pretty sure that it has something to do with this stupid computer. I really wanted to try out linux os since I am new to this but this computer only wants me to use windows.

---

### Post by oldfred on 2013-04-18
Messed up does not help us. What specifically are the issues.

Does live mode work and can you do most things in live mode?

Is your Windows 7 in MBR(msdos) using all 4 primary partitions, or a newer one with UEFI?

If you can get to terminal in live mode, post this.

       sudo parted /dev/sda unit s print

---

### Post by illmattic on 2013-04-18
I might have found what the problem is. I was able to get it working when I started in windows first and then ran the installation process. It would reboot it for me and then it would give me the option of windows or ubuntu and when I clicked ubuntu it goes straight into the live version and I can see the desktop program to install ubuntu 12.10. When I do that and I get the option to either install it inside of windows 7, replace windows 7 or something else I chose inside windows 7 and then something would go wrong and it would say the installation process was aborted. So that I tried it again and clicked the something else option. And when it shows the data or whatever its called it shows the sliver of green, then the large block of orange then next to it a large block of free space but unlike I saw on the tutorial videos there was a tiny block of blue to the right of that. And when I went to go add to the free space it says its unuseable. I'm guessing thats what the problem is.

---

### Post by oldfred on 2013-04-18
If you download the Windows installer that is wubi.
Wubi does not work with Windows 8 pre-installed systems that use gpt partitioning and now can only be installed from inside Windows, not from liveDVD.

But with wubi you do not have to repartition. It is just like another program running in Windows, relies on the underlying NTFS partition and the Windows boot loader. As such it should not really be used for long term installs, but ok for test to see if you like Ubuntu.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by illmattic on 2013-04-21
Ok. I unstalled the wubi version. I want to use Ubuntu as my main OS and just use Windows when its my only option. Ubuntu wouldn't boot when the live-dvd is in so I went to my boot options and booted it manually. Then the purple screen came up with that sign that shows at the bottom of the screen where you need to press the space bar so I did. Then it loads to the normal screen. I checked if the dvd had any defects and it didn't. So I went to install Ubuntu and instead of choosing install inside windows 7 I went to something else and the condition is the same. The free-space partition says its unuseable. I'm assuming this is the problem?

---

### Post by oldfred on 2013-04-21
Almost all Windows 7 systems use all 4 primary partitions. You have to delete one, so you can make an extended partition which can hold many logical partitions.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by illmattic on 2013-04-21
IT WORKS! Thanks alot for your help I really appreciate it. I have Ubuntu up and running alongside Windows. But I have a problem. When I try to load up files onto Ubuntu from a cd, it says that the cd is blank but I know its not because it works fine on Windows. I want to transfer some files I had on my Windows OS to Ubuntu using these cds and dvds.

---

### Post by illmattic on 2013-04-21
Also now I can't connect to the wireless internet. No wireless connection options come up?

---

### Post by oldfred on 2013-04-21
Do not know about CD issues. 

Have you updated system. If you have a wired Ethernet, you need to update and it may install your wireless driver or in system settings, Additional drivers may be a choice to install drivers. But there have been many threads on some models of wireless. You can search forum for your model or post this info in a new thread.

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post a new thread and attach (via the advanced edit top panel paperclip icon) the abs-network.txt file which will be in your home folder.

---

### Post by illmattic on 2013-04-22
The issues are now fixed. Thanks alot for your help!

---

