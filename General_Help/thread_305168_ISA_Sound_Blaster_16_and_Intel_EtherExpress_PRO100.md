---
title: "ISA Sound Blaster 16 and Intel EtherExpress PRO/100 don't work/not detected"
date: 2006-11-22
forum: General Help
---

### Post by jordoex on 2006-11-22
I recently reinstalled xubuntu edgy after installing win98 and win2000, for a triple boot, so i can also run dos/windoze games and use nt kernel required apps without fiddling with dosbox or wine.  All other times i installed, my ethernet port wasn't plugged in, so the installer never detected any network interfaces.  This time I had it plugged in and it still didn't recognize anything.  However, windoze could connect to the internet just fine and run my sound card.
Here are my comp's specs:
Pentium 2 (Klamath)
128MB ram
Brilliant I V1.XX motherboard(now called BrillianX, manufactured by QDI) -- Award BIOS

Intel EtherExpress:
IRQ=10, I/O=x0280-x029F
I have put e100 and eepro100 into /etc/modules; they insert properly but don't work.(see following dmesg file)

Sound Blaster 16(windows says AWE compatible)
IRQ=5, DMA=1 and 5, I/O=x0220-x022F, x0330-x0331, x0388-x038B
I've tried both snd-sb16 and snd-sbawe but neither work.(see following dmesg file)

It seems like a problem with ISA cards.  I might try to get a PCI card.

At least i can download the .debs in windows or use my flash drive to tansfer them(i keep this comp in my room and bring the box upstairs and connect it to get updates.) and then easily double click them in edgy to install them. Good work xubuntu team!:D  I was always annoyed about that in dapper.

---

### Post by jordoex on 2006-11-23
bump

---

### Post by jordoex on 2006-11-24
more info, i installed some isa/pnp utils and this is what they said: (look at attachment) notice that it doesn't include any of the specified I/Os

---

### Post by jordoex on 2006-11-29
bump

---

### Post by mgmiller on 2006-11-29
I don't think ISA cards can be auto detected by anything.  They don't communicate with the the bus the way PCI cards do.  If you have pci slots, try installing a pci sound card. You can probably find something compatible at newegg.com for US $18-$20 or so. They have some as cheap as $8.00.  You may have better luck getting an inexpensive mobo with integrated sound and networking.  If you're not into gaming, even an integrated video card.  Of course you would also probably need a new cpu and ram for it, and possibly a new power supply.  Damn, that starts to cost a few bucks.

---

### Post by Campitor on 2006-11-29
Have you tried:
 
```
modprobe snd-sb16
```
 
That worked for me...
 
Camp

---

### Post by jordoex on 2006-11-30
if you were to look at the boot.messages.txt you'd see this
```
[   99.473201] Sound Blaster 16 soundcard not found or device busy
[   99.473241] In case, if you have non-AWE card, try snd-sb16 module
[   99.589970] Sound Blaster 16 soundcard not found or device busy
[   99.590003] In case, if you have AWE card, try snd-sbawe module
```
that's me trying to initialize snd-sbawe and snd-sb16 with /etc/modules
it's the oddest thing ever

i tried 2 'auto detection' utils, pnp-isa tools and scanport, whicah came with something else(possibly didn't work cuz i got them from debian repositories and not Ubuntu repos). And as for there not being anything that can autodetect isa cards, how does windows do it? The NT Kernel uses a HAL too.

Also, I just scanned over the output of hal-device and it didn't explicitly say if there were either of the isa cards registered.  There were a couple of "General ID for reserving resources required by pnp motherboard registers" and and unknown intel device and the isa bus and the pnp bus and the system speaker.  
The problem probably has to do with the motherboard or the kernel or the BIOS.  I might contact the mohterboard manufacturer although it probably won't help.

---

### Post by aditya.ma on 2007-10-25
Hi I noticed your issue and decided to do a little searching regarding soundblaster 16 ISA support.
it would seem
creating a file in 

/etc/modprobe.d/name of driver

with specific card options in this example

sudo nano /etc/modprobe.d/snd-sb16

when nano opens you have two choices
if your card is set to default put in:

options snd-sb16 isapnp=0

otherwise this should work, tweak for efficiency :)
options snd-sb16 index=0 id="SB-16" port=0x220 mpu_port=0x330 irq=5 dma8=1 dma16=5 isapnp=0

save the newly created file 
Last step FINALLY! :
sudo modprobe snd-sb16

you can try it without sudo

works fine.. good luck :)

---

### Post by jordoex on 2007-10-25
Yeah... i don't think I'll really be able to test that out... I haven't used that computer for almost a year and now it's just sitting in a corner in my room.  The p3 in my house has one, but that hasn't been booted up in a while.

---

