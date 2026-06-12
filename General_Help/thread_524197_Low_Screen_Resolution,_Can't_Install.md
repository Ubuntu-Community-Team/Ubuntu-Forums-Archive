---
title: "Low Screen Resolution, Can't Install"
date: 2007-08-12
forum: General Help
---

### Post by Miniberger on 2007-08-12
I'm trying to run the Ubuntu Live CD on a friend's laptop, but without much success. 

So, I put in the Live CD and it boots to the first menu (the one with the option to start/install ubuntu, along with a number of other options). So, I choose the first one - start/install ubuntu. It goes into the loading screen where the bar bounces back and forth, then comes up with the error "can't access tty; job control turned off." I searched and found this to be a very common error and there was no clear solution.

One solution I found was, while in the first menu, to press F6 while "Start or install Ubuntu" is selected, then add "all_generic_ide " to the beginning of the "Boot Options" line of text. After doing this and pressing enter, some lines of text appear showing all of the systems being checked.

Then, an error appeared saying:

"[98.###000] uvc video Failed to query (135) uvc control 1 (unit 0) -32 (exp. 26)

uvc: Failed to initialize the device (-5)

hda_intel : azx_get response switching to single_cmd mode"

Ubuntu  loads accompanied by the familiar welcoming noise, but the screen was strangely off. 

I then decided to try and load in safe graphics mode. Again, I typed in "all_generic_ide " and Ubuntu loaded, but this time with graphics. However, all of the graphics were not only low resolution but also didn't act regularly.

The largest problem here was that when I tried to install, I couldn't see the "Next/Back" buttons at the bottom of the window and I couldn't get them to come on to the screen. I tried moving the window to the top but it simply would go no further. I could interact with the language menu, which was visible, but icons that were off screen were useless and I couldn't get them to appear.

So because I can't interact fully with the GUI, I can't proceed with the install. If anyone knows how to fix this, or the "can't access tty; job control turned off" error, the help would be greatly appreciated.

---

### Post by Miniberger on 2007-08-12
System Information:

Dell Inspiron 1520
Intel Core 2 Duo
2GB RAM
160 GB SATA HDD
128MB NVIDIA® GeForce™ 8400M GS  
Windows Vista Home Premium
Trying to Install Feisty 

I've tried changing the screen resolution but can get no higher than 800x600.

I'm trying to install the latest updated version of Feisty i-386.

---

