---
title: "Windows installation not accessible after Ubuntu installation"
date: 2013-05-03
forum: General Help
---

### Post by Soulcrusher on 2013-05-03
I love tinkering with ubuntu every once in a while but I am terrified to install ubuntu since it always messes up the boot partition with grub and everything. I want windows to boot by default and have ubuntu boot only when I want to but I can't seem to work this out.[SUP]1[/SUP] This has kept me from installing ubuntu for quite some time.

I finally decided to give ubuntu a go on my laptop and I am at it yet again: Ubuntu has installed grub and I am unable to boot windows anymore. I first tried installing 12.10 with wubi so I could maintain my windows bootloader (trying to avoid grub) but after installation neither Windows or Ubuntu was accessible. After firing up my Windows recovery stick I could get back into windows but ubuntu still failed to boot. I noticed the wubi installer hadn't created a partition for Ubuntu so I gathered it didn't install properly (little did I know it just creates a giant file on the selected drive).

The next thing I tried was to boot from the live cd and install ubuntu again. So I chose the same disk as before (I planned the ssd for windows and the hdd for ubuntu), resized the windows programs partition and created a partition for Ubuntu as well as a swap partition. I selected to install the bootloader on the hdd since I wanted to keep the windows partition untouched and the laptop is supposed to boot from the ssd anyway. The result is that it now boots up grub where I can select between Ubuntu as well as three (!) options for the same windows partition. So I booted into windows, downloaded easybcd to try and get the ssd as boot drive again and have windows boot by default. The result is that I now can't boot windows at all.

The last thing I tried was using boot repair in ubuntu, but that doesn't give me the desired effect. While it does remove most of the unnecessary duplicate Windows entries from Grub, the problem still remains. [I have created a boot info summary with boot repair]("http://paste.ubuntu.com/5629975/") and would like to know what I need to do next. I was thinking about removing the boot partitions on both drives and try to run boot repair from a live usb, but it will probably ruin everything. Can anybody help me to get the following:
1. have the boot sector on the ssd (1st drive/sda) so I can still boot windows when the hdd is removed in case of a hdd failure.
2. have it boot windows by default and have the option of booting ubuntu.
I really don't care which bootloader as long as it just works.

Some extra info regarding my system: The ssd should only hold windows, the hdd has another windows partition for programs, a bitlocker partition as well as the stuff ubuntu put on it.
The laptop is an Samsung 300V3A with a crucial M4 64gb ssd and has the dvd drive swapped with a western digital 750gb hdd in a caddy.

Note [SUP]1[/SUP]: I accomplished this earlier by removing the windows disk while installing Ubuntu and then use the bios to select which os to boot. The downside was that the Ubuntu installation set back the windows clock by 2 hours. Not something I was happy with at all.

I really hope someone can help me with my situation.

---

### Post by Frogs Hair on 2013-05-03
Wubi creates a Ubuntu root disk/folder inside the windows partition so it won't be visible as a partition from windows disk management though windows will detect an unknown operating system. If this is windows 8 you are writing about there are complications with Wubi.      [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by Soulcrusher on 2013-05-03
Thanks for the input.

I have removed Wubi from Windows since I was not able to boot into it anyway. The windows uefi file got messed up afterwards so I can't boot into windows anymore. The linux version I have installed now is from the live disk.

---

### Post by Frogs Hair on 2013-05-03
See my signature for Ubuntu documentation. [URL="https://help.ubuntu.com/community/UEFI"]
https://help.ubuntu.com/community/UEFI[/URL]

---

### Post by Impavidus on 2013-05-04
> **Soulcrusher said:**
> 
Note [SUP]1[/SUP]: I accomplished this earlier by removing the windows disk while installing Ubuntu and then use the bios to select which os to boot. The downside was that the Ubuntu installation set back the windows clock by 2 hours. Not something I was happy with at all.

This clock thingy at least can be solved easily if it occurs again: [http://ubuntuforums.org/showthread.php?t=2133337](http://ubuntuforums.org/showthread.php?t=2133337). It shouldn't happen when you install with the windows drive attached, as the Ubuntu installer will fix it then automatically.

---

### Post by Soulcrusher on 2013-05-04
Frogs Hair: I was looking for that exact page, but trying the things there didn't work. Boot repair said I needed to create a partition for uefi_boot or something, I did that but it still said the same thing.

So I have gone ahead and did a fresh reinstall of both windows and ubuntu. Everything is now set up correct aside from one thing: Impavidus, the linux installation has set the bios time to utc yet again :P
Anyway, thank you both for the help :)

---

