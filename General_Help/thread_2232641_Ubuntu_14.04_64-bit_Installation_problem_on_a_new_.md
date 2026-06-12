---
title: "Ubuntu 14.04 64-bit Installation problem on a new PC (UEFI)"
date: 2014-07-03
forum: General Help
---

### Post by quantumhd1337 on 2014-07-03
Hello

So I wanted to install ubuntu on a separate drive just for my testing. On my previous machines (All of them were equipped with old BIOS) it was easy and painless(Little note I was using 32-bit versions only back then). A few months ago I upgraded my parts so now my motherboard has UEFI and I will include all the specs now but before I do that I will explain the problem. To put an image of ubuntu to USB stick I use Universal USB Installer program. I want to install the 64 bit version of ubuntu 14.04 but the moment It engages the GUI I have just one giant artifact on both of my displays. I tried to download the 12.04 LTE that I used previously but the same thing happens. I tried to disable the iGPU but then If I remember correctly is spits an error Kernell-Panic or something like that. I can try and make a photo of that if you think it might help. I have no Idea what's wrong. 

P.S I forgot to mention that in my PC Secure Boot was enabled but I disabled it so the windows still works fine but still the same errors occur.

Specs:

CPU: Intel Core i5 4670k
GPU: XFX Radeon 7970/ Sapphire 7970 VAPOR-X (Crossfire)
RAM: 8 GB 1333 mhz
Motherboard: Asus Z87-Pro

---

### Post by sudodus on 2014-07-03
Welcome to the Ubuntu Forums :-)

I would try another tool (than Universal USB Installer). For example you can try ***Unetbootin*** or some other tool from this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Maybe you can get some tips from the following links (and links from the first link)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by grahammechanical on 2014-07-03
2 displays? Try it with only 1.  Try using the nomodeset option. We are talking about first running the live session, are we not? Or have you installed Ubuntu?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Please give more detail on the GPU setup. It is hybrid graphics?

Regards.

---

### Post by quantumhd1337 on 2014-07-04
[COLOR=#282828][FONT=helvetica]So I removed my sound card that I forgot to mention, both gpu's and I tried to launch it from the igpu. It worked and I was able to install the system. After that I booted the system and It looked like everything was ok. Then I re-installed all the hardware again and now I can only see a cursor and a black screen so I am not even able to install the drivers. Any more ideas?[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]P.S That sound card is Asus Xonar DX if it matters.[/FONT][/COLOR]

---

### Post by sudodus on 2014-07-04
Obviously the problems are caused by a card, and I would guess the Radeon graphics card. Try to boot in text mode (with the [boot options]("https://help.ubuntu.com/community/BootOptions") **nomodeset **and **text**) and then try to install a proprietary driver. I have no own experience of proprietary drivers for Radeon Crossfire cards, so please wait for someone else to give you those details.

---

