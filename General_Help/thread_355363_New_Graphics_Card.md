---
title: "New Graphics Card"
date: 2007-02-07
forum: General Help
---

### Post by Mark76 on 2007-02-07
A friend sent me an old graphics card he no longer needed and I'd like to know (a) IF I can use it with Ubuntu and (b) how.

The card is a Maxi Gamer Cougar (made by Guillemot.  I think).

---

### Post by renzokuken on 2007-02-07
apparently its based on the nVidia Riva TNT2 M64 chipset so should be fine. 

make sure you find out whether you need legacy nvidia drivers or not before attempting to install nvidia-glx

---

### Post by dcstar on 2007-02-07
> **Mark76 said:**
> A friend sent me an old graphics card he no longer needed and I'd like to know (a) IF I can use it with Ubuntu and (b) how.

The card is a Maxi Gamer Cougar (made by Guillemot.  I think).

Change your /etc/X11/xorg.conf file to use the **vesa** driver, install the card and run:
```
sudo dpkg-reconfigure xserver-xorg
```
If it is auto-detected then it may well work!

---

### Post by Mark76 on 2007-02-07
If I install the card before doing that the wizard doesn't work.  If I don't install it the wizard thinks I want to install a driver for my motherboard graphics card.

---

### Post by Mark76 on 2007-02-07
Okay, I managed to get the wizard to work with the card installed.  But then it asked me a load of questions I didn't know the answer to, so I just said okay to the first choice I was given for each one (except the vesa and xorg ones) and I've had to reinstall Ubuntu from scratch.  Including the two hour update from Breezy to Dapper

---

### Post by Mark76 on 2007-02-08
Can someone walk me through the process of changing from Xorg to Vesa?

---

### Post by renzokuken on 2007-02-08
it easy, but you explained it wrong. just for clarification, xorg is the software side of grafix that uses a specified driver. in this case, you want to change your xorg.conf so that it is using the vesa driver instead of another.

go to a terminal and type the following

```
sudo gedit /etc/X11/xorg.conf
```

this will bring up a text editor with you xorg.conf in.

go down to the part where it says Section "Devices", it should look something like this, dont worry if it is slightly different

```
Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce PCX 5750]"
    Driver         "nvidia"
EndSection
```

you want to change the line (note it could be "radeon", "ati" or a whole host of others instead of nvidia here, dont worry about the Identifier either)

```
Driver     "nvidia"    (or whatever is in the place of nvidia)
```

to

```
Driver     "vesa"
```

close and save the file, then press Ctrl+Alt+Backspace to restart the xserver and start using the vesa driver

EDIT: i just thought about something else. before you installed the new card, were u using a standalone grafix card (PCI or AGP) or were you using onboard grafix? if you were using onboard grafix (a chipset on the motherboard), then you may have to change a setting in the BIOS to get the mobo to use the new card

---

### Post by Mark76 on 2007-02-09
I was using an onboard graphix

---

### Post by renzokuken on 2007-02-09
well in that case you may have to change the bios settings to use your new off-board card. it may be that it autodetects it but without knowing which motherboard you have there is no way of telling.

did you have a manual with the motherboard?

EDIT : here is a random post i found via google.....its vague but it should apply in a similar manner.

> 1-on the earlier motherboard i used to set the BIOS to search for the graphics adaptor from PCI slot first,it would then look for the adaptor; first PCI,second AGP and third On-board and run whichever it found.Setting to on-board first it would never find the AGP adaptor and always run its default ie the on-board graphics.


---

### Post by Mark76 on 2007-02-09
Nope

Second hand computer.  All I know is it's a Compaq (and you know how much detail THEY give you on the casing :p )

---

### Post by renzokuken on 2007-02-09
lol true......well get into the bios and see if you can find any options for VGA or videa or something like that......

dunno what the compaq bios key is but its probably F2, F4 or Del

---

### Post by Mark76 on 2007-02-09
I think it's F10.

That's the option that comes up when you switch the computer on, anyway.

---

### Post by renzokuken on 2007-02-09
yeah thats the bad boy.......well have a look around the bios, dont change anything yet though, and report here what you see.

---

