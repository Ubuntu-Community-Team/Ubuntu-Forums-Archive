---
title: "[SOLVED] Medion akoya e2215t - how to install linux?"
date: 2018-03-19
forum: General Help
---

### Post by dylanhameleers on 2018-03-19
I want to install linux ( lubuntu or linux mint ) onto my e2215t because windows uses too much of my 32gb disk space and too much ram ( 2gb ).

I have tried several things but nothing worked due to uefi. My bios/uefi ( confused ) doesn't let me boot from external usb stick or anything else that is not windows on my c:\ partition... 

I turned off secure boot and i still can't boot from usb stick, while i'm sure it IS bootable... I used rufus and i have tried almost every linux distribution.

Plop bootmanager doesn't work somehow.
Grub2win fails everytime when booting from an .iso file saying : "must load kernel first" or "*****.iso not found".

Please help me.

- Dylan

---

### Post by Topsiho on 2018-03-20
Hi,

I am not sure, but I have that hunch that you did not burn your Lubuntu as an image to your usb-stick or DVD, but copied the .iso file instead.
So you have to be sure you burn that .iso file as an image first, and then try and boot from the usb-stick (or DVD).
From an .iso file it's impossible to boot.

Topsiho

---

### Post by dylanhameleers on 2018-03-25
Hey, thanks for the reply!

i wanted to reply yesterday but the forums were doing silly and wouldn't let me log in...

i used rufus to create a bootable usb. and my pc did start from it, but my laptop didn't. that's the problem.


- Dylan

---

### Post by Topsiho on 2018-03-25
If the pc boots and the laptop doesn't, the problem must be in the laptop.
If it has more usb-ports, you might try one of the other ones.
Maybe you need to alter the boot sequence, so that the laptop boots from usb if a bootable usb stick is present.
If that doesn't help, I am out of wits :)

Topsiho

---

### Post by mörgæs on 2018-03-25
The solution seems to be adding baytail-bootia32.efi (sic) to a 64 bit ISO as described [here]("https://community.medion.com/t5/Notebook-Netbook/E2216T-Linux-installieren/td-p/37427").

The 32/64 bit mixed setup is a workaround for hardware designed to be unfriendly to Linux. There is no technical benefit from implementing EFI in hardware this way.

---

### Post by dylanhameleers on 2018-08-07
After giving up.. A long time later.. I did what u said ( didn't come back to this site cuz rage quit lol ).. But after install the sound doesn't work ( Ubuntu ) I get dummy output :/ Ubuntu is the only linux that works on this laptop.. I'm close to a replacement but I have to know how to do this! :)

---

### Post by mörgæs on 2018-08-07
There's no need to consider a replacement. I suggest that you mark this thread solved, follow these [instructions]("https://wiki.ubuntu.com/Audio/AlsaInfo") and open a new thread in Multimedia with the Alsa results.

Your rage shouldn't be directed towards Ubuntu but a company which forces hardware to be easily accessible by only one operating system.

---

### Post by dylanhameleers on 2018-08-13
Thanks! :)

---

