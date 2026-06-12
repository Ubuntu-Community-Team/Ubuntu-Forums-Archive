---
title: "OS won't boot even an fresh install"
date: 2017-11-29
forum: General Help
---

### Post by Vitor_Hugo on 2017-11-29
Hello people, 

i had a problem somedays ago -> [https://ubuntuforums.org/showthread.php?t=2378665](https://ubuntuforums.org/showthread.php?t=2378665)

I tried to fix the problems, googling for answers and checking other threads here and there, i can't fix it , seems my problem

is diferent, i see a thread with many solutions but the op had to give some answers to the contributors and my case maybe diferent,


my os was Lubuntu i downloaded xubuntu, the last one x86 and do a installation ,formatting the hdd checking the option to delete all os ,

but this is happening , again
 [IMG]https://i.stack.imgur.com/2mV1H.png[/IMG]



this is not my image, it's from google images but the message that appears is this, the boot wont boot after this no matter the time

that i wait, the buttons that i press, this message appears on my previous os too.

it only boot choosing recovery mode ! any advice ?


thank you

---

### Post by irv on 2017-11-29
If this was a new install, I would just try another fresh install and maybe even from a new download. It sounds like something went wrong with the install.

---

### Post by oldfred on 2017-11-29
What brand/model system?
What video card/chip?

Have you tried recovery mode? In advanced options in grub menu.
If only one Ubuntu install, you need to hold shift key from BIOS to grub menu, if BIOS.
Or if UEFI, you have to press escape key perhaps several times from UEFI but before grub menu.

---

### Post by Vitor_Hugo on 2017-11-29
> **irv said:**
> If this was a new install, I would just try another fresh install and maybe even from a new download. It sounds like something went wrong with the install.

Hello,
Hum... maybe i will try in the weekend doing it again.

> **oldfred said:**
> What brand/model system?
What video card/chip?

Have you tried recovery mode? In advanced options in grub menu.
If only one Ubuntu install, you need to hold shift key from BIOS to grub menu, if BIOS.
Or if UEFI, you have to press escape key perhaps several times from UEFI but before grub menu.


Yes, it only boots in recovery.

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


Thank you !

---

### Post by oldfred on 2017-11-29
That is an older Intel internal video chip.
How much RAM do you have?
You may work better with Lubuntu if less than 3 or 4GB of RAM.

 Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by Vitor_Hugo on 2017-11-30
Hello, yes it's an old pc, i googled before and i confirmed that lubuntu was more lightweight, but in this pc idk why xubuntu it's faster... when i open for a web browser and some tabs with works better than lubuntu, it's strange.... my previous os was lubuntu i had to uninstall it because this same error, and because it was very slow whenever i opened firefox (no addons, no plugins, no extensions, only defaults) 
System has 1gb ram :O
I will try again doing a fresh install .

thank you

---

