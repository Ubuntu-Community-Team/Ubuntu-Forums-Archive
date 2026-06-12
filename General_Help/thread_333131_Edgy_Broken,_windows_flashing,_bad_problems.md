---
title: "Edgy Broken, windows flashing, bad problems"
date: 2007-01-06
forum: General Help
---

### Post by Exillo on 2007-01-06
Note: I might not be able to remember what happened exactly and in the right order, I'll do my best.

Hi all,

I decided to install Beryl so I did that and it was working well. I decided I didn't really need the extra eye-candy so I logged out and went back into Gnome. It showed the splash screen and then the UI for a brief moment before flicking to the system colour (the colour that is the background of the gnome loading splash screen).

I had to just press reset on my computer. When it loaded back up I went into xgl which was going very slow (not the special effects but logging in and doing general things). This got me even more worried, I opened up Swiftfox and the top bar (with the title and the minimize, maximize, close buttons are) wasn't there. 

Now I'm a little foggy here but I, quite weirdly, decided to try Kubuntu at this time so I entered **sudo apt-get install kubuntu-desktop**. I realised it was starting a large download which I didn't want so I closed the terminal and restarted the comp then went back into Xgl. Now everything is going very slow and I can barely open anything. Swiftfox doesn't really open and it likes to come up with error messages and when I get applications running the top bar of the app flashes rapidly.

(I am posting this on my dual-boot XP).

This is really bad and any help would be massively appreciated. :KS :(

PS. I'm not that sure what caused these problems so that's why I've made a new topic in the general help section.

---

### Post by GrumpyBob on 2007-01-07
I'm using Beryl, and every once ina  while this happens to my desktop.  Usually if I log out and back in again the problem is resolved.  Not entirely sure what's responsible.  If you login and select gnome as your session, all should be OK.

Robert

---

### Post by Exillo on 2007-01-07
Logging in and out doesn't work (well I can't do that in Xgl or Gnome anyway) and resetting it doesn't work and when I try going into Gnome it shows the splash screen and then the UI for a brief moment before flicking to the system colour (the colour that is the background of the gnome loading splash screen) and I have to reset the comp.

---

### Post by Exillo on 2007-01-07
Any other suggestions? :(

---

### Post by Rich78 on 2007-01-07
In grub choose Ubuntu version (recovery mode).

Let it boot to the console and type:

sudo apt-get remove beryl emerald-themes

Hopefully this should fix the problem, although you may well get an XServer error.

If so I can look up how to fix that or you could try reinstalling beryl by going back to the recovery mode and in the console typing:

sudo apt-get install beryl emerald-themes

Hope this helps :D

---

### Post by Exillo on 2007-01-07
I removed beryl emerald-themes then typed exit and logged into Xgl. The problem still existed but I right clicked on the red emerald icon and pulled back to the gnome mode (can't remember exactly what it was called) which fixed the problem. I then quit Beryl and removed it from the Xgl startup. 

My problem is fixed in Xgl apart from Firefox / Swiftfox taking a very long time to start although that was a problem I faced beforehand and don't know how to fix either. 

EDIT: Just tried going into a Gnome session, works perfectly (apart from Fire/swiftfox problem). :D

Thanks guys for the help. :D

---

