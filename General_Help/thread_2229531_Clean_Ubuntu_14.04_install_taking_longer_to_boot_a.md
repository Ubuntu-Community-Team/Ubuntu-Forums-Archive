---
title: "Clean Ubuntu 14.04 install taking longer to boot after kernel upgrade"
date: 2014-06-13
forum: General Help
---

### Post by mvburgos on 2014-06-13
[COLOR=#333333][FONT=UbuntuRegular]Hello this is my first post. I own an Asus Chromebox (2gb ram, 16 gb sdd, 3.0 usb ports) and fresh installed Ubuntu 14.04 x64.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I decided to upgrade kernel because I was experiencing some freezing issues with XBMC,[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So first i installed stable kernel 3.14.04 from mainline and boot time was fine (it booted very fast I would say about 5 seconds) then after a while I installed kernels 3.15 and 3.14.06 BUT this time I also removed OLD STOCK KERNELS (dunno if that has something to do) after that the problem began, boot time is taking way longer, I would say about 30 seconds.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Finally today I installed kernel 3.14.07, set grub to boot with that by default but same thing :([/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I post boot.log and dmesg, hope it is correct for this matter, if you need any other log just let me know.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][boot.log]("https://db.tt/igcNhItG")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][dmesg]("https://db.tt/Re1VhqTZ")[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-06-13
How many kernels do you have now? If you have more than one may be try booting and logging into all the non default ones and then see if boot time improves for the default kernel. I have never had issue with boot time, but sometimes after a kernel update log in kind of takes a while and the trick above fixes the problem for me.

I use mainline kernels (3.15 now) but always keep the latest stock kernel.

---

### Post by mvburgos on 2014-06-13
I hace 3.14.07 and 3.15 installed, tried every combinación and still the same. I think it is because I removed the stock kernels. In that case how can I revert to the default boot or what was the stock versions so I try installing the latest one and test. Thanks!

Will an apt-get upgrade dist help in this case?

---

### Post by monkeybrain20122 on 2014-06-13
You can install it back easily. Look into synaptic, search for linux. There are four packages for each kernel version (linux-image generic, linux-image extra generic, linux-headers, linux-headers generic)

---

### Post by mvburgos on 2014-06-13
Hmm I just tried that but it brings many packages and its confusing, in the mainline kernel webpage I usually download 3 .deb files: linux-headers generic, linux headers all and linux-image generic. Can you confirm kernel 3.13.0_29 is the latest stock, if not which number version is?

---

### Post by monkeybrain20122 on 2014-06-13
It would pull in four packages, the mainline kernel doesn't have linux-image-extras (required for some hardware). I can't confirm the kernel version as I am now on 13.10.

Edited: the package "linux" should have the latest stock kernel.

---

