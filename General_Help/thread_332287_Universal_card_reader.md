---
title: "Universal card reader"
date: 2007-01-05
forum: General Help
---

### Post by steel_lady on 2007-01-05
A dumb blonde needs to mount CF card in the universal card reader Soyntec 66 in one. It recognizes SD card but completly ignores CF card. Is there anything that can be done since I don't have drivers for linux and it says it is linux compatible?

---

### Post by fragos on 2007-01-06
You're smart enough to choose Linux and that's more than I can say for most computer users.  You haven't told us what distrobution you're running so I'll assume Ubuntu 6.10.  I appoligize if I'm going over things you already know how to do.  First we need to open a terminal window.  Look at the upper left hand corner of the screen and click the word "Applications".  Move the cursor to "Accessories" and in the menu that pops up click "Terminal".  Enter the command "uname -r".  It'll display the version of the kernel you're running and I want to know that.  Plug your card reader into a USB port.  Enter the command "lsusb".  One of those lines should show your card reader and may say "Soyntec".  We've just insured that the system can see your reader.  Now enter command "ls /media" and you'll a list a list of devices as in "cdrom hda1 hda2" or something like that.  Now place an SD card in the reader and again "ls /media".  There should be another device on the list, perhaps "sda1".  Now put a CF card in the reader and "ls /media" again.  Another device should be on the list and you should still see the one added for the SD card.  I'll want to see the ouput of the "ls /media" commands.  With that information we'll determine what to do next.

---

### Post by nix4me on 2007-01-06
most times, those all in one jobbers can only read 1 type of media at a time.   Not sure if you were trying the CF while the SD was in, but that could be the problem if thats the case.

nix4me

---

