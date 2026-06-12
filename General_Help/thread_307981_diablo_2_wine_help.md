---
title: "diablo 2 wine help"
date: 2006-11-27
forum: General Help
---

### Post by Jack of Fables on 2006-11-27
diablo 2 has 3 discs, "install disc", "play disc", and "cinematics disc"
you have to put in thw install disc first, but when i open it with wine it says i need to insert the install cd, even when its in. but when i click ok, it says it again. if i click cancel it tells me that i it couldn't find the cd or something. do i need to configure anything firwst, if so, how?

---

### Post by ~LoKe on 2006-11-27
As far as I can remember, the only way to do this is to copy the CD's to your hard drive and mount them.

---

### Post by Jack of Fables on 2006-11-27
thanks for replying, i have copied all three discs to my home directory, but don't know how to mount them

---

### Post by epennings on 2006-11-30
I just tried to install Diablo II myself. There is no need to copy the cd's to your harddrive. I'm using wine version 0.9.26 from the winehq repository. If you haven't done so already add this to your /etc/apt/sources.list :
```
## Wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

Perform the following commands to remove any old versions of wine, and install the new one:
```
sudo apt-get update
sudo apt-get --purge autoremove wine && rm -rf ~/.wine
sudo apt-get install wine
winecfg
```

You will probably get some warning or fixme messages, they can be ignored usually. In winecfg go to the "Drives" and click AutoDetect. This will detect any cdrom,floppy,usb and hd drives you have.

Exit winecfg and insert the Diablo II install disc.
Type the following commands to start the install:
```
cd ~/.wine/drive_c
wine /media/cdrom/install.exe 
```

Install the game like you would under Windows, except:
- Choose "no" when asked to create a desktop shortcut
- When you see the progress bar, but nothing happens, dont worry! There is actually a prompt hidden behind it but you just can't see it. Install the discs in this order : play,cinematics,install (wait for the discs to load and press <ENTER> to start installing)

The same applies to Diablo 2:LoD, except install the discs in this order : play, expansion

If you have the original game you can load Diablo II without any further modifications, but you have to keep your expansion disc in the cdrom-drive. I can update the game to the latest version, play over battle.net etc.

The only problem is the sound, I haven't figured out how to get that working yet properly (i just hear a lot of noise), but if you turn it off it runs great.

Good Luck :D

---

### Post by newagelink on 2006-12-01
So is this issue still unresolved, as far as no sound in Diablo II goes?

---

### Post by epennings on 2006-12-02
I managed to get sound working properly. I have changed the audio settings in winecfg like this:

---

### Post by fycloops on 2006-12-14
This didn't work for me but it was promising because I got sound during intro and then hissing during gameplay. So I just changed the defauly sample rate to 22050 and all is sweet so far.

Ferg

---

### Post by PrairieShaman on 2006-12-25
thank you for this how to! I am installing as we speak! it's a little tricky to get it to start installing because you can't bring that window up that tells you to insert the disc, but its going now!

I found out at the family xmas get together that my cousins son plays Diablo II and we were talking about it and he asked if I wanted to play with him sometime so here we are, installing Diablo II to play along with the 9 year old son of my cousins. :)

---

