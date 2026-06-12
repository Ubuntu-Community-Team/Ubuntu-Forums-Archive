---
title: "How can I change Screen Resolution from command line?"
date: 2008-06-27
forum: General Help
---

### Post by MasterJ37 on 2008-06-27
I was messing around with different screen resolutions, when I chose one that was too big for my monitor, and now when I start up Ubuntu, all I see are alot of lines. I need to change my screen resolution back so I can use ubuntu again.:(

---

### Post by Pjotr123 on 2008-06-27
Do this:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

That should do the job.  :-)

---

### Post by krelverehan on 2008-06-27
I would get warm to this forum post down below.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Good luck!

---

### Post by avtolle on 2008-06-27
I'd try the link that Pjtor123 posted. Generally, under 8.04, the old standby ```
sudo dipkg -reconfigure xserver-xorg doesn't work as it did before, given the new "bullet proof X" now being used. It basically asks a few questions about the keyboard, and that's it.

Try this, if booting into recovery mode and trying to fix X from there doesn't work: boot into safe-graphics mode and from the terminal[code]gksudo displayconfig-gtk
```, find your monitor, check to be sure the correct graphics card and driver are in use, apply by hitting <Enter>. Restart your system (easiest way to do this for most folks) and see if the changes took.

---

### Post by MasterJ37 on 2008-06-27
I'm using 7.10, and when I did that something like this came up:
(gksudo:4089) WARNING** :Cannot open display
I can't remember the whole thing if there's more. right now I'm just stuck using Windows ME. could you get me a code that would just change my resolution to 800*600?

---

### Post by Pjotr123 on 2008-06-28
> **MasterJ37 said:**
> I'm using 7.10, and when I did that something like this came up:
(gksudo:4089) WARNING** :Cannot open display
I can't remember the whole thing if there's more. right now I'm just stuck using Windows ME. could you get me a code that would just change my resolution to 800*600?

Better to switch to 8.04, by means of a clean installation (with previous formatting; don't use the upgrade button). 8.04 is much better than 7.10.

However, for 7.10 this is the old method:
Applications - Accessories - Terminal
type:
sudo dpkg-reconfigure xserver-xorg

press Enter.

Agree immediately to every proposed answer, don't make any different choices. Use the following keys: Tab, Space bar, arrows, Enter.

Afterwards do a full reboot.

---

### Post by j0n0th0n on 2008-06-28
Is there a way to chance Screen Resolutions from a command line?  

I am looking for a way to script changes to resolution and refresh rates so that my games are in sync with the desktop.  This avoids flicker that I was experiencing with at lease one game, NWN.

Thanks
-J0n0th0n

---

### Post by MasterJ37 on 2008-06-28
Thank-you, problem solved.

---

### Post by MasterJ37 on 2008-06-28
why don't you just change your desktop resolution, so you won't have the problem?

---

### Post by j0n0th0n on 2008-06-29
> **MasterJ37 said:**
> why don't you just change your desktop resolution, so you won't have the problem?

That sir, is a great question. 

Short:
I am in fact doing that manually when I start a game such as NWN or UFO AI. 

I would like to avoid this manual process.

LONG:
The answer lies in my cheep HANNS-G wide screen 17" LCD monitor.  Until I get a new one, the monitor currently only handles the games desired sync rates at 1024x768. When the desktop and game are out of sync I get the annoying flicker.

Also, I like running the desk top at 1280x720 but the max refresh rate is an odd 59 Hz at that resolution.  

The desktop at 1024x768 is also strange in that it has a the bottom  section of the screen that is just not being drawn.  

I am 
ok with: the answer being no.
Better with: the answer being "go dust off some esoteric app., xyz" 
Extremely happy with : here is the command and syntax...
Amazed with: here is the command, script I wrote for you, and a cup of coffee while you wait for your game to start. ( not holding the breath on these last two.  :) )

---

### Post by MasterJ37 on 2008-07-03
Well, I'm not the person that's able to help you in this case, so I sugest that you open a new thread with a unique title, and state your problem. Good luck. I'm sure you'll find the answer.

---

### Post by sujoy on 2008-07-03
use xrandr from command line to change resolutions

---

