---
title: "i restarted X11"
date: 2007-01-05
forum: General Help
---

### Post by finer recliner on 2007-01-05
im new to linux.

i have ubuntu (dapper drake) installed, and i accidentally pressed ctrl+alt+backspace, which restarted X11.

now the only resolution that's available is 640x480. what happened to my desktop resolution?? how do i "undo" whatever i did?:confused: 

thank you in advance.

---

### Post by darrenm on 2007-01-05
Don't know why it changed your res.

Just reboot the PC and you should be fine.

---

### Post by finer recliner on 2007-01-05
> **darrenm said:**
> Don't know why it changed your res.

Just reboot the PC and you should be fine.

umm i forgot to mention i already tried that :(

---

### Post by hostage on 2007-01-05
hello im newbie too but i think i can help u. 

First of all, are you using NVIDIA card, if so!

go to the terminal and wrote

**sudo gedit /etc/X11/xorg.conf**  

and in the configure file add the resolution that you wish to use for example "1024x768"
and save the config file.

This is how my configure file look like. as u can se i just added "1280x1024" and saved it and
 went to "System/preferences/screen resolution" and changed it.
___________________________________________________________________________________________________________
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      **"1280x1024"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      **"1280x1024"** "1024x768" "800x600" "640x480"
_________________________________________________________________________________________________________

---

### Post by rovernaut on 2007-01-05
I had a prob once too. This is what I did on Kubuntu, I presume Ubuntu gnome would be similar.
 Fixed by  menu>system settings>Computer admin >Monitor display, there I changed the setting back

---

### Post by finer recliner on 2007-01-05
i have an ATI card.

when i go to manually change the resolution through the system menu, the only option listed is 640x480. normally i should have up to 1680x1050.

still need help please!

---

### Post by hostage on 2007-01-05
okey if u have ATI then i can't help u but try to find some confige file to change
the resolution. ?! There must be some kind of a Ati configuration file somewhere?

When i installed my nvidia card i realized that the only resolution opition i had was " 640x480" 
but then i added "1280x1024" in my confige file and saved it then it was visible in the system menu screen resolution.

sry my english aren't very good. Im from sweden..... well, i hope you get the resolution back.

---

### Post by finer recliner on 2007-01-05
isn't there a an x11 settings file backed up somewhere that i can revive? idk, i still need help with this please.

---

### Post by hostage on 2007-01-05
No there is no X11 file backed up unless u have made a backup.

---

### Post by finer recliner on 2007-01-05
problem solved (for anyone else who needs help):

i found this site
[http://en.wikibooks.org/wiki/Guide_to_X11/Configuring](http://en.wikibooks.org/wiki/Guide_to_X11/Configuring)


in which i followed the commands for debian users to reconfigure X11. most stuff was auto-detected, and now i'm back to my normal resolution.

i also made a backup of my current /etc/X11/xorg.conf in case of future problems :)

---

### Post by ~LoKe on 2007-01-05
> **hostage said:**
> No there is no X11 file backed up unless u have made a backup.

Sure there is.  /etc/X11/xorg.conf~ will be created when you edit the file.

---

### Post by finer recliner on 2007-01-05
solved (again):

turns out there was still a problem lurking in my system. when i tried to run an application that involved rendering (my screensaver and a game, neverball) the framerate was rediculously slow. sooo

i followed the commands on this site [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and now im all good again :)

@~Loke: isnt /etc/X11/xorg.conf~ only created when you *manually* edit the file.? in this case, i did not (and i dont see it in my directory)

---

### Post by stanthecaddy22 on 2007-01-05
~xorg.conf will be created if you edit the file with certain editors (eg. emacs) but is not an automatically created backup by the system. I recommend keeping backups of any config file you change, just so you have an untainted version to go from.

---

