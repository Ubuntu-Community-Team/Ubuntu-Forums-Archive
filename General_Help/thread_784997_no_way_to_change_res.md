---
title: "no way to change res?"
date: 2008-05-07
forum: General Help
---

### Post by Helios38 on 2008-05-07
hello,


i am installing ubuntu for a friend who wanted to try it out. the install went smooth, no hitches or anything, but heres where i run into my problem.



when i log in, i obviously see that the res is not config'ed correctly. 800 x 600.


ok, no prob. i know the monitor of his was capable of 1024 x 768, so, i start searching the application menu for screens and graphics (this being 8.04, its different than in gutsy)



it wasnt there :confused:


so i searched preferences, administration, nothing.


i even opened "screen resolution" tool in preferences, to change the res, but it insists that the screen is only capable of 800 x 600.


i checked the xorg.conf file, and all it gave me in the monitor section was "configured monitor"


the gfx chip in an intel 810E

any ideas on what the heck happened? its worked on other systems, i was able to get that "screens and graphics" option before, but this time, its gone :(

---

### Post by y0umebednow on 2008-05-07
yeah i have the same problem. i got to the screen and resolution from file system > usr > shared or app or something like that and a whole bunch of icons come you can find screens and resolution in there. you might be able to change it by selecting your driver and such but i had no success :/

---

### Post by aquavitae on 2008-05-07
I've had similar problems with every distro I've tried - Hardy is the first distor I haven't had this problem with!  I usually fix it by editting xorg.conf by hand, but if you don't know how to do this, try running *dpkg-reconfigure xserver-xorg*.  I think you have to shut down the xserver when you do it, so easiest is to restart in recovery mode and then run it. It will bring up a text based wizard to customise the xserver.

---

### Post by plucky on 2008-05-07
In a Terminal window try ```
sudo displayconfig-gtk
```

Good Luck

---

### Post by Helios38 on 2008-05-07
will report the result of this. thanks

---

### Post by Helios38 on 2008-05-07
> **plucky said:**
> In a Terminal window try ```
sudo displayconfig-gtk
```

Good Luck

this worked. thanks.
:)

---

