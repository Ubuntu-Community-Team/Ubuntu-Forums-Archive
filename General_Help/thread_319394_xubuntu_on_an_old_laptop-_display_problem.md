---
title: "xubuntu on an old laptop- display problem"
date: 2006-12-15
forum: General Help
---

### Post by eliwis on 2006-12-15
Hello, ive just installed xubuntu on my old Fujitsu E330 laptop with 64mb of RAM, and it works pretty good except the desktop which doesn't show up on all of the screen and there are a lot of horizontal lines crossing the screen. my guess is that there is something wrong with the graphics card driver but i dont know what else to do. any help will be very appreciated.

thank you

---

### Post by kerry_s on 2006-12-15
Info! What kind of graphics card? From what spec's i could find, it looks like you have to use 16 bit color, i'm not sure about the size, some say max is 800x600 others say 1024x768.

In terminal do ->
sudo gedit /etc/X11/xorg.conf  
(you can copy and paste, middle click to paste)
look for->
	DefaultDepth	24

change to

	DefaultDepth	16

look for->
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

change to

	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

if that don't work go lower->

	SubSection "Display"
		Depth		16
		Modes		"800x600" "720x400" "640x480"
	EndSubSection

ctrl + alt + backspace to restart X

---

### Post by eliwis on 2006-12-16
(misspelled it, sorry)

Edit: Hey! thanks a lot it worked

---

### Post by Sef on 2006-12-16
> Thank you for your answer, when i open this file i have nothing written in it, maybe it is corrupted or something?

Are you sure you did not mistype something?

---

