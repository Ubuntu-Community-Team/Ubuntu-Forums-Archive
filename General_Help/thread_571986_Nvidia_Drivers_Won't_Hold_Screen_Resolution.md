---
title: "Nvidia Drivers Won't Hold Screen Resolution"
date: 2007-10-09
forum: General Help
---

### Post by Hawkeye05 on 2007-10-09
I Installed The Restricted Nvidia Drivers on my GeForce 4 MX, I can get the resolution to 1280x1024 (what i want) but after each restart it reverts back to 1024x 768 Ive included my xorg.conf file any help is greatly appreciated

---

### Post by Phearicle on 2007-10-10
Try googling it:lolflag: and make sure your operating system version can properly work with the resrticted drivers

---

### Post by Hawkeye05 on 2007-10-10
i would assume feisty would work alright,

it works great except for after a restart when it reverts

---

### Post by oodledoodle on 2007-10-10
try editing the screen section of your xorg file to look like this
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes     "1024x768" "800x600" "640x480"
    EndSubSection
```
removing the first two un-needed resolutions may fix it. you can do this by entering the following in a terminal window
```
sudo gedit /etc/X11/xorg.conf 
```

---

### Post by Nachowarrior on 2007-10-11
type "info nvidia-settings" into your terminal... there's an article explaining that it's intentional that it doesn't preserve the settings even when just logging out or switching users because different users may have different preferences or some crap like that. I didn't read up on a fix, but that may point you in the right direction... or just type in "nvidia-settings" in terminal and set it up every time you restart... or figure out someway to auto run it every time you start up the bun. :-p

---

### Post by American_Outcast on 2007-10-11
I had to run sudo nvidia-settings in the terminal for it to save it to my xorg.conf When I tried to click on it from the menu I had the same problem you are now having. Just create a back up of your /etc/X11/xorg.conf file to be on the safe side, (I made three when I first did it. I am paranoid that way, lol.)

---

### Post by jwcgator on 2007-10-11
> **American_Outcast said:**
> I had to run sudo nvidia-settings in the terminal for it to save it to my xorg.conf When I tried to click on it from the menu I had the same problem you are now having. Just create a back up of your /etc/X11/xorg.conf file to be on the safe side, (I made three when I first did it. I am paranoid that way, lol.)

Wow, that worked, I've been searching for a solution for a long time now  Thank you Oh so much.

---

### Post by American_Outcast on 2007-10-11
> **jwcgator said:**
> Wow, that worked, I've been searching for a solution for a long time now  Thank you Oh so much.


Your welcome. I am glad I could help.

---

