---
title: "PS/2 and USB mice usage under Xubuntu."
date: 2007-02-05
forum: General Help
---

### Post by alxwind on 2007-02-05
Hey gurus,

I set up Xubuntu on old PC in my basement. I need it to broadcast video stream to a TV in my living room upstairs and also be a regular desktop for everyday needs like web-surfing, emails, spreadsheets etc. It has a Radeon 9200SE video with video out port (yellow rca?) and connected to ps/2 mouse and keyboard via usb adapter. I need those to navigate to my videos to watch them on the TV. I don't have a spare kb and a mouse yet so I took those ones downstairs to use them while installation.

Installation went fine, all the hardware was detected perfectly. Obviously these ps/2 kb and a mouse were recognized as generic ps/2 devices according to xorg.conf file.

After all the set up tasks were done I unplugged kb and the mouse, took them upstairs, hooked them to the usb adapter and... nothing! I can use them connected to PS/2 port but not as USB devices. What a pity!

After some googling I found out what causes the problem — xorg.conf. It has a section just for ps/2 mouse and keyboard but not for usb ones. 

You would suggest — install your damn xubuntu while upstairs. Impossible. I had to hack xorg.conf file after OS is installed in order to get my tv-out working otherwise I wouldn't get a picture on the Tv at all.

All I need is just some instructions how to add usb kb and mouse support to my xorg.conf file so can use ps/2 input devices AND usb ones.

This part of my xorg.conf file with input device sections:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,ru"
        Option          "XkbOptions"    "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
        Option          "XkbVariant"    ",winkeys"
EndSection
        
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

That's what I have in my /dev/input folder

```
tv@tv-desktop:~$ cd /dev/input/
tv@tv-desktop:/dev/input$ ls
by-id  by-path  event0  event1  event2  mice  mouse0  ts0
tv@tv-desktop:/dev/input$
```

Where to? Please, please, please.

---

### Post by alxwind on 2007-02-11
well, i solved the problem after recompiling the kernel and selecting all Keyspan devices support under USB Support sectiong in menuconfig. Lack of drivers for my adapter was the issue. :)

---

