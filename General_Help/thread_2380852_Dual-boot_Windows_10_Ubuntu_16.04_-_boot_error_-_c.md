---
title: "Dual-boot Windows 10 Ubuntu 16.04 - boot error - can no longer boot via usb"
date: 2017-12-22
forum: General Help
---

### Post by jerry42570 on 2017-12-22
Hello. I've googled this issue extensively and it is clear that I need to run Boot Repair. Unfortunately, when rebooting my PC I see the usb stick light up, or hear the external DVD drive run but it never boots off of either. I only get to the screen that says "Minimal BASH-like line editing is supported." Is there any way from this menu that I can change the boot order? My laptop is a Samsung Odyssey running Windows 10 (UEFI) with windows on the SSD. I installed Ubuntu on the HDD - at least that's where I created the partitions for it.

After installing I was able to boot into Ubuntu just fine - I had the GRUB menu that I'm accustomed to seeing with the options to use Ubuntu or Windows, with maybe two other options that I never used. I updated it and installed some applications. After the update I was prompted to restart and that's when I first saw the screen that I am on now.

Thank you in advance for any assistance or suggestions.

---

### Post by oldfred on 2017-12-22
Can you still get into UEFI and boot Windows?
Did you install Ubuntu in UEFI boot mode?
What video card/chip does your system have?
Does it boot if you type 'exit' (without quote) at bash error?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]

---

### Post by jerry42570 on 2017-12-23
Thank you so much for your fast reply. To answer one of your questions - [COLOR=#000000]Does it boot if you type 'exit' (without quote) at bash error?
[/COLOR]Why yes! Yes it does! Can't believe the answer was so simple :)

Thank you so much! So relieved that I don't care how embarrassing it is that I didn't notice that same question in other replies to similar situations :P

---

### Post by oldfred on 2017-12-23
You still need some repair, may just be reinstall of grub or something else.
Summary report or perhaps repairs from Boot-Repair may be all you need. 
But best to have some one here review report first.

---

