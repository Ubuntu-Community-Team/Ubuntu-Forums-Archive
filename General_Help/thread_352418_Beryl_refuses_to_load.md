---
title: "Beryl refuses to load"
date: 2007-02-03
forum: General Help
---

### Post by championchap on 2007-02-03
I just gave Beryl ago on my new Edgy installation, though it didnt work at first.. stupid me forgot to install the nvidea drivers! haha

anyway, got that sorted out afterwards.. installed the drivers (not the beta) and tried out Beryl.
It worked!! For a while.. then it froze.. and now i cant start Beryl up again

the window decoration dosnt appear and i cant click anything..

When i type beryl-manager i get some detection message come up in the terminal, and then at the bottom i notice this.

checking for GLX_EXT_texture_from_pixmap: failed

any suggestions? Please bear in mind that im fairly new to this.. and might need to be babied through some things.

---

### Post by Waappu on 2007-02-03
Hi

Press ALT+F2 and type beryl-manager.
Right-click red gem on notification area and Select Window Manager -> Beryl

---

### Post by championchap on 2007-02-03
No, you misunderstand.. maybe i wasnt very clear before.
Beryl worked once, but it crashed.. then i restarted the computer and now it wont start up properly.

The red gem appears when i type beryl-manager into the terminal
but it then removes all the window decorations and stops me being able to do anything with it at all

the error that comes up in the terminal after i type beryl-manager in comes at the end of some compatability check t performs.

The problem is this

check for GLX_EXT_texture_from_pixmap: failed

what can i do to solve this?

---

### Post by shironeko on 2007-02-03
> **championchap said:**
> No, you misunderstand.. maybe i wasnt very clear before.
Beryl worked once, but it crashed.. then i restarted the computer and now it wont start up properly.

The red gem appears when i type beryl-manager into the terminal
but it then removes all the window decorations and stops me being able to do anything with it at all

the error that comes up in the terminal after i type beryl-manager in comes at the end of some compatability check t performs.

The problem is this

check for GLX_EXT_texture_from_pixmap: failed

what can i do to solve this?
Are you sure that Xorg is configured correctly and that the following options are enabled?

Thats for AIGLX and Ati graphic Card:

Edit xorg.conf by typing sudo gedit /etc/X11/xorg.conf
Section "Device": THe following must be enabled (written without #)

Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"

Also, at section server layout:

Option          "AIGLX" 	"true"

And at the end of the document be sure to have written:

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
       Option "Composite" "Enable"
EndSection

---------------------
Well.... I should have asked you what graphic card you have... :P
If it's ATI, be sure to use the open driver, not the propietary one and follow the instructions above.

---

### Post by championchap on 2007-02-03
Ive got an nVidia 7600GT
I take it i shouldnt follow those instructiosn then?

Edit: Ohh, i just managed to get into the settings manager without it crashing on me.. and i dissabled anything that i had enabled just before it crashed.
After a couple more crashes.. it seems that its the blur effect thats causing me grief!

I guess if i ignore that effect we can count this one as resolved.. but if any of you know what the trouble might be there id appreciate it.

---

### Post by david_2001 on 2007-02-03
The blur plugin seems to be broken for (some) nvidia users.  How I found out:
[LIST=1]
[*]Enabled the blur plugin after reading this thread
[*]Got a total system freeze
[*]Reset
[*]Logged back in to home account but just got a blank screen
[*]Rebooted into maintenance mode
[*]Edited ~/.beryl/settings and disabled the blur plugin
[*]Googled for "beryl blur freeze" and found a thread in the Beryl Forum about the blur plugin not working properly with nvidia cards since beryl 0.1.5.  (There's also a note in the Beryl WiKi about the blur plugin "failing gracefully" if it won't work with the installed video card!)
[/LIST]
Anyway, that'll teach me to be curious!  Otherwise, I really like beryl.  I didn't even have to edit my xorg.conf to get it working.

---

