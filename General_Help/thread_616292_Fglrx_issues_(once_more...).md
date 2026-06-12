---
title: "Fglrx issues (once more...)"
date: 2007-11-18
forum: General Help
---

### Post by anemon on 2007-11-18
Sorry for pestering you all with this worn old subject, but at least there's a new twist to it: Gutsy Gibbon. Yesterday, I finally got around to making a fresh install of the new 7.10, and everything worked just fine, even using the proprietary graphics drivers from ATI which were proposed by the system during the last phase of configuration. There wasn't even any problems with the fancy integrated Compiz effects! 

Then I noticed that Google Earth would freeze on startup. And before I found the workaround, I wanted to check if my 3D acceleration was activated. So I entered
```
glxinfo | grep direct
```
into the terminal, and ***OOOPS!*** the screen just went blank (wrong resolution and/or refresh rate) and stayed that way even after reboot. I still can't figure out what happened, but I did manage to save the day by booting from CD and editing my xorg.conf manually to use the "ati" drivers. Only now everything seems rather sluggish and the Compiz effects are deactivated.

So the question is: how do I get back to where I started? What's the command for running the automatic config again?

---

### Post by derby007 on 2007-11-18
1st off : see if you can revert to an older xorg.conf in your /etc/X11/ folder, there should be one there if there had been changes done to the original.
My experience is: graphics card is ATI X1300 Pro, Live CD wouldnt boot into graphical mode, I had to use the AlternateCD & edit xorg.conf. I then went into the 'menu' to select the proprietry driver, (it asks for 'xorg-driver-fglrx' to be installed), then install 'xserver-xgl', reboot & I had compiz working. I now have to install compiz-manager.

---

### Post by anemon on 2007-11-18
That's the wierd thing: there was no backup of xorg.conf to revert to! And as far as I know, the command I ran shouldn't meddle with the file at all. No idea what happened there...

I guess I could just open the Restricted Drivers Manager and enable the flgrx driver again. I'm just worried I'll end up with the exact same problem! :-( 

Oh well.

---

### Post by derby007 on 2007-11-18
As far as I'm aware that command definitly doesnt meddle with your xorg.conf. 
I wonder if this is your problem >>  'Then I noticed that Google Earth would freeze on startup' : Google application finding an error with your graphics maybe, screen resolution, what graphics card do you have?

---

### Post by anemon on 2007-11-18
Yep, that's just it. And I found that thread, and the workaround, and fixed it. So Google Earth is no longer a problem.

And just now, I tried to activate the restricted drivers again, and everything works just fine! :-) Except for one thing: when I try to enable visual effects in System > Preferences > Appearance, the system gives me the following error message: "The composite extension is not available."

How do I make it so?

---

### Post by derby007 on 2007-11-18
Do you need composite-extensions? I thought I saw another thread saying not to bother, do you have direct-rendering working: 'glxinfo | grep direct' ? 

If you do need composite :: Try this: (from another thread):

First, run sudo gedit /etc/X11/xorg.conf

"Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card..."

---

### Post by anemon on 2007-11-18
Ok, I tried editing my xorg.conf again, this time changing the "0" to a "1" in the "Extensions" section. Graphics still work! But when I try to enable the effects, I get yet another error message: this one just tells me that "the effects couldn't be activated" or something like that. Which is wierd.

I don't think I need any additional packages or drivers, since it worked like a breeze when I first installed Gutsy yesterday. And running "glxinfo | grep direct" is what caused the problem! Don't wanna go there again... ;-)

---

### Post by derby007 on 2007-11-18
Go on, give it a go..........in for a penny in for a pound !! 
Actually: did you reboot, or Ctrl-alt-backspace to restart graphics after you updated xorg?

---

### Post by anemon on 2007-11-18
Yep, I did the ctrl-alt-bckspc thingie. After that, I got the new, less informative error message.

But OK, I tried "glxinfo | grep direct" again. Hold your breath! Phew, nothing bad happened. And direct rendering is supposed to be activated. But still no fancy desktop FX...

---

### Post by derby007 on 2007-11-18
What do you mean by : 
> But still no fancy desktop FX... 

Have you installed the compiz-manager to choose all your effects?

see: [http://wiki.compiz-fusion.org/CCSM]("http://wiki.compiz-fusion.org/CCSM")

---

### Post by anemon on 2007-11-18
OK, I tried your last lead as well: the "xserver-xgl" package. And after another xserver restart, I've got the FX working again! Thanks a lot, derby007!

But what the heck happened to begin with? Still a mystery...

---

### Post by derby007 on 2007-11-18
some Mysteries will never be solved.......sit down now, relax, have a few pints of Guinness (from the fridge) and later on try & install Mythtv, now theres a way to get a headache........this is where the Guinness comes in handy, ie. to ease the pain of installing :)  :)

---

