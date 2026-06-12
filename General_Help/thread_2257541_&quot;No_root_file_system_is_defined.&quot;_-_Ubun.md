---
title: "&quot;No root file system is defined.&quot; - Ubuntu installation problem"
date: 2014-12-20
forum: General Help
---

### Post by mario46 on 2014-12-20
Hi everyone.


So I was trying to install Ubuntu and I stumbled upon this problem...
To be completely honest I don't know much about Ubuntu in the first place. 
First of all, I downloaded Ubuntu from Ubuntu's official site. (I think it was the 14.10 version)
Once it was done I extracted it, I ran Wubi application...
A menu popped up asking me for a username, password, disk space etc...
I filled it and clicked OK. So it started downloading/installing, not really sure...
Once it was done, it asked me if I wanted to restart the computer now or later.
I clicked Restart now and once it restarted Ubuntu logo showed up and finally the startup menu showed up.
It said "Installing" in the pop up bar and suddenly a message appeared saying: "No root file system is defined."
All I could do was to click "OK" and that's pretty much it... I restarted the computer and I got to choose between Windows 7 or Ubuntu (I was running Win 7 before obviously), but when I click on Windows 7, it won't start and when I click on Ubuntu same thing happens. I tried running Demo version of Ubuntu when booting and it worked fine. I saw an app called "Install Ubuntu" so I clicked on it and I would choose to install Ubuntu over Windows 7 but installing would go on forever with no progress bar showned. 


I really don't know what to do so please help. I would very much appreciate any replies.


Mario

---

### Post by Sef on 2014-12-20
> [COLOR=#000000]I ran Wubi application...[/COLOR]

Wubi is not longer supported.  Please use Ubuntu located [here]("http://www.ubuntu.com/download").

---

### Post by mario46 on 2014-12-20
That is the one I downloaded. Version 14.10, but when I open it, there is only Wubi that can be opened

---

### Post by oldfred on 2014-12-20
Did you really want to overwrite Windows?
Most prefer to dual boot until they have some experience with Ubuntu.

Not sure if you completed install or not, as that error message is usually from the Something Else installer where you did not specify or create a / (root) partition.

May be best to see details:
Post just link to summary report, do not run auto fix until someone has reviewed details.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by hakuna_matata on 2014-12-20
[QUOTE=mario46]
It said "Installing" in the pop up bar and suddenly a message appeared saying: "No root file system is defined."
[/QUOTE]
IMHO, it is [bug 1385930.]("https://bugs.launchpad.net/wubi/+bug/1385930")

_Recommendation:_ Try an install without Wubi
If this is not what you want, a [workaround is possible]("http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861").

---

### Post by Impavidus on 2014-12-21
> **mario46 said:**
> That is the one I downloaded. Version 14.10, but when I open it, there is only Wubi that can be opened

You don't extract the .iso, but you burn it to a dvd or usb drive and boot from it. I don't know why the wubi.exe file is still included on the disk image, but better not use it.

---

