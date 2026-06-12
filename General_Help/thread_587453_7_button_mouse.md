---
title: "7 button mouse"
date: 2007-10-22
forum: General Help
---

### Post by goodmore on 2007-10-22
I need help w/ clear instructions to solve my last issue w/ Ubuntu. I want to have the side buttons on the mouse be back and forward. 7.1 finally installs w/ the wheel scrolling, but I miss surfing with the back button.

---

### Post by Saibot on 2007-10-22
This worked for my Logitech MX1000 mouse.  You need to edit your /etc/X11/xorg.conf but you should always back it up before making changes.
Open a terminal, type ```
sudo gedit /etc/X11/xorg.conf

```

find this section and make these changes.  You might need to change the number of buttons to what your mouse really has, but I'm not sure how critical that is.
I really wish something this simple would be setup by default, but that's just me.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"     #changed this from  "ImPS/2"
	Option		"Buttons"	"12"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option          "ButtonMapping" "1 2 3 6 7"     #add this line
EndSection
```

disclaimer - I'm no expert, but this has always worked for me in the past.

---

### Post by linuxwizard on 2007-10-22
Check over this see if it will help you.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by goodmore on 2007-10-22
Thank You very much. I had it all but the buttonmapping line. That did the trick. So long Windows.

---

### Post by Pahanilmanlintu on 2007-10-23
On a side note, does anyone know why aren't the extra buttons still not configured by default? It's always the same hassle with getting them to work every six months.

---

### Post by Boobo-oobo on 2007-10-24
TNX Saibot, that did the trick . . .

---

### Post by LashSilence83 on 2008-02-29
I tried to do this and it seemed to completely mess up my xorg file and caused strange problems with the settings daemon. Perhaps I could have not followed directions properly but I did copy exactly what was previously posted and I even tried it again following the docs on the official ubuntu site with similar results. Now I'm afraid to mess with the file too much until I have a better grasp of what it was I did wrong.

---

