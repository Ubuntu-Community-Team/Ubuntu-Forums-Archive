---
title: "system settings shows the wrong soundcard"
date: 2007-03-02
forum: General Help
---

### Post by hempa on 2007-03-02
Hello i have had troubles with my sound and i think i know why. i have a Creative Sounblaster Audigy  soundcard but when i check in system settings->Hardware->Display it says: sound card Vesa. Driver Vesa. and there is a option where i can change manufacturer and driver, i found creative, and there was a couple of choises for their cards but i could not find my soundcard in that list. is there a way i can add it to the list?? i would also like to add emu10k1 to the drivers list

---

### Post by taurus on 2007-03-02
Do you have an onboard soundcard?

---

### Post by hempa on 2007-03-02
Sorry this might sound stupid but how can i find out if it it is a onboard card or not??

---

### Post by taurus on 2007-03-02
Either go into the BIOS and check or run this command from a terminal and post the output here.

Applications  -> Accessories -> Terminal
```
lspci
```

---

### Post by hempa on 2007-03-02
Ok this is what i got.

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 0106: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
0000:04:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:04:02.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:04:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04

---

### Post by hempa on 2007-03-03
so how should i go on from here??

---

### Post by Guitar Man on 2007-03-12
:guitar: Try the commands below [COLOR="Blue"]in blue[/COLOR], at the # prompt friend (it may work, it may not)

Looks like your sound card is a Creative Labs Sound Blaster Audioligy (PCI.)

You may have another card "stealing" the sound (my CX8811 WINTV card did this)
the S17012 is my AC97 sound card
The Conexant modem may be in there as default sound device? - at the top of the list

root@mycomp-desktop:/home/mycomp# [COLOR="Blue"]asoundconf list[/COLOR]
Names of available sound cards:
CX8811
[COLOR="Red"]SI7012[/COLOR]

now chose a card name from above which looks like it might be the Creative Labs SB card:-

root@mycomp-desktop:/home/mycomp# [COLOR="Blue"]sudo asoundconf set-default-card[/COLOR] [COLOR="Red"]SI7012[/COLOR]
root@mycomp-desktop:/home/mycomp# 

reboot now (DON'T just restart x-session, reboot)

Hope that worked

---

