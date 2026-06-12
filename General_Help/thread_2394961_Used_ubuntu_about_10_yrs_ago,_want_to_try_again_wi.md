---
title: "Used ubuntu about 10 yrs ago, want to try again with new build, buuutt...."
date: 2018-06-24
forum: General Help
---

### Post by lunaz on 2018-06-24
...stupid games made me go back to windows xp then 7! Also I forgot most of whatever I did before :( :(

**_CURRENT HARDWARE_**

I have 1 desktop pc running windows 7.
[LIST]
[*]a 120gb SSD with windows & path of exile on it. i have 7gb left :(
[*]a 1tb mechanical HDD with all my documents & other software installs, 2 partitions
[*]DVD drive
[*]geforce something video card (~4 yr old)
[*]headset with mic for music & games
[*]HDMI monitor, keyboard, mouse
[/LIST]

I have a synology NAS that just backs up stuff to 2 1tb drives daily, no cloud whatevers or servers on it
Cable modem, router, NO printer

**_SOFTWARE NEEDS_**

Path of exile with the following things:
[LIST]
[*]yolomouse
[*]MercuryTrade (runs on java)
[*]PoeTradeMacro (runs on autohotkey)
[*]Acquisition
[*]Path of Building
[/LIST]

Otherwise I just use email client, browser, sftp client, irfanview image editor & notepad++, occasional steam game & keepassportable

_**MY QUESTIONS FOR NOW**_

[LIST=1]
[*]I was thinking of getting a 1tb SSD with my next build & dual booting windows 10 on it for games & ubuntu for everything else, but would that put wear & tear on it restarting all the time?
[*]Still reading pretty mixed reviews about getting games running on linux. Anyone here get PoE running on it without much work?
[*]What about still backing up to the NAS? DO I have to start over or will those work with mixed platform?
[*]Any hardware that 'just works'? What about getting my data off the backup drive to a new one & having it accessible to both windows & linux?
[/LIST]

---

### Post by yancek on 2018-06-24
If you only have 7GB of free space on the SSD, forget about that it is not enough.
You can install to the 1TB external, something you can't do with the windows installer.  You can then install the Ubuntu Grub bootloader to the MBR of the 1TB drive and update-grub and then set this drive to first boot priority in the BIOS to boot either Ubuntu or windows 7.  Or you can install Grub to the MBR of the SSD.  Better to use the option to install to the 1TB.

If you have an Nvidia Geforce graphics card, you will probably have to install proprietary drivers after the install.  Not really a problem.

I've never heard of any of the software you mention.

Windows is good for games, some of them have success on windows but I don't game so have no idea.

If you get windows 10, that changes everything and I would suggest you read carefully the link below which is the Ubuntu documentation on the subject.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dragonfly41 on 2018-06-24
I will just throw in a nugget of knowledge I learned when I setup a
dual boot Windows 10 + Ubuntu 16.04.

I try to avoid using Windows 10 but in my foray into that OS I saw an option to install Windows Linux Subsystem. 
This allows Ubuntu to be embedded within native Windows.

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

I don't use it much, but if you are installing Windows 10 first you could use this to become familiar with Ubuntu.

My choice would be to keep Windows and Ubuntu separate and install Ubuntu into a separate drive.

---

