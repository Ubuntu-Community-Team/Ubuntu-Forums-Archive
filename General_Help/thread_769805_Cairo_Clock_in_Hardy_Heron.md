---
title: "Cairo Clock in Hardy Heron"
date: 2008-04-26
forum: General Help
---

### Post by adohall on 2008-04-26
Has any one else noticed that the Cairo Clock display is awry on startup (set through system/sessions) but fine if launched after startup form applications menu?

This wasn't an issue in gutsy.

---

### Post by highgeere on 2008-04-29
I am having this issue as well. In addition, the movements of the clock hands is jerky regardless of how it is started. I've tried reinstalling the package, but that's about the only thing I could think of. Is this widespread, or do adohall and I just have funky configurations?

---

### Post by csa on 2008-05-02
I'm having the same problem... I recently upgraded from gutsy 7.10 to hardy 8.04.  Cairo clock used to work fine with gutsy... but now, every time I start a new session, cairo clock is all deformed.  If I start cairo-clock after startup then, there's no problem.

I tried resizing the clock, and it works as long as it is after startup, but then, everytime I restart my computer, the clock is all deformed again.  It looks like a bigger clock within a smaller square.

Also... I noticed that if I start cairo-clock from terminal, I get:

*(cairo-clock:10416): libglade-WARNING **: could not find a parent that handles internal children for `vbox'*

I don't get it...  I tried uninstalling and installing a different version, but no success....  I now have cairo-clock version 0.3.4, but I tried with 0.3.2, and it was the same...

I'd appreciate some help, since I've run out of ideas now...

---

### Post by csa on 2008-05-02
Ok... so I haven't been able to fix the issue with Cairo Clock, but... here's what you can do to get around it...

go to synaptic, search for and install *screenlets*. Once it's installed, open the terminal and type:

~$screenletsd --gui

It'll open a window with different widget like applets.  Select "Clock" and then check the box on the bottom right corner that says "Auto start on login". Then click on "Launch/add"

It will launch a desktop clock.  Right click on the desktop clock and select "properties".  Then... under "themes" select "Cairo clock", and then, under "options" you can select the size, position, time zone, etc...

It works if you want a nice clock on your desktop.  You can also select multiple clocks and adjust them for different time zones, and there are also other widget-like mini applications that you might like to make your desktop more aesthetic...

Of course, if it works and you want to use this clock instead of cairo-clock, then make sure to uncheck cairo-clock from system>preferences>sessions

Anyway... like I said, it doesn't solve the cairo-clock problem, but it's a nice alternative...

cheers...

---

### Post by highgeere on 2008-05-06
I also wanted to mention my fix for this, since it has allowed me to continue using cairo-clock. I removed my cairo-clock entry from 'sessions', first thing. Then I created a very simple script, similar to this:

sleep 20
cairo-clock &

It's extremely quick and dirty, but it works so I don't care. Name it cairo_start.sh or something, give it execute perms, add it as an entry in 'sessions', and you will have a functional cairo-clock a few seconds after the rest of your startup apps load. I still don't know what is happening that is breaking the clock, but it is obviously loading prior to a dependency, or something similar.

---

### Post by klange on 2008-05-06
Wasn't Cairo-Clock virtually abandoned? Screenlets is based entirely on Cairo-Clock, and for all intents and purposes, the "Clock" screenlet *is* Cairo-Clock, even has the same theme.
On top of that, Screenlets is in active development and there are no problems with the Clock.

---

### Post by itsjustarumour on 2008-05-09
Hi All,

Not sure how I missed this thread the first time round, but I've also been having trouble with the Cairo Clock on Hardy (worked fine with Gutsy on the same box).  I've posted up a screenshot at [http://ubuntuforums.org/showthread.php?t=781419](http://ubuntuforums.org/showthread.php?t=781419)  Is this the same as you guys have been getting?

Cheers,

itsjustarumour

---

### Post by itsjustarumour on 2008-05-09
> Wasn't Cairo-Clock virtually abandoned?

Nope, MacSlow's website at [http://macslow.thepimp.net/?cat=9](http://macslow.thepimp.net/?cat=9) states that the latest version (0.3.4) was only released on February 28th, 2008, so looks like its still very much an active project  :-)

---

### Post by itsjustarumour on 2008-05-11
OK, heres how far I've got.  I've tried both version 0.3.3 from the Hardy repos and 0.3.4 from Macslow's site.  They produce slightly different results, but still broken!  Heres the screenshots:

---

### Post by itsjustarumour on 2008-05-11
> **highgeere said:**
> I also wanted to mention my fix for this, since it has allowed me to continue using cairo-clock. I removed my cairo-clock entry from 'sessions', first thing. Then I created a very simple script, similar to this:

sleep 20
cairo-clock &

It's extremely quick and dirty, but it works so I don't care. Name it cairo_start.sh or something, give it execute perms, add it as an entry in 'sessions', and you will have a functional cairo-clock a few seconds after the rest of your startup apps load. I still don't know what is happening that is breaking the clock, but it is obviously loading prior to a dependency, or something similar.

I've tried the above fix, and it works perfectly - HOWEVER: 

...I now have TWO incidences of the Cairo Clock running, one looking good and one broken one like in my previous screenshot.  And whatever I do, I can't stop the broken one appearing when my Desktop loads...  I've tried uninstalling Cairo Clock and deleting all config files (well, all the ones I could find anyway) and reinstalling, but it keeps coming back to haunt me! :shock:

So - there must be a config file somewhere thats launching the "broken" clock again - but where???  What am I missing?!

---

### Post by itsjustarumour on 2008-05-12
Bump.  Anyone?

---

### Post by itsjustarumour on 2008-05-13
Yay, I've just managed to fix the problem! :guitar:

The config file I was looking for is /home/ian/.gnome2/session . I deleted the line for "Cairo-Clock" and everything is working fine again. Looks like there may be some issues with gnome-sessions-properties and the way in which the Sessions Manager GUI writes to the session file - I'll investigate further when I get the chance and maybe file a bug report.

:-D

---

### Post by leonardo_neo on 2008-11-01
Sorry to bother you guys after such a long time. I tried to fix the problem with the scrip as mentioned above, but it didn't help in my case.

Kindly please tell what to do? Or what file to delete as mentioned in above reply?

---

