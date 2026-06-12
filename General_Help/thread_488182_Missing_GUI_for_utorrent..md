---
title: "Missing GUI for utorrent."
date: 2007-06-29
forum: General Help
---

### Post by Eric the Grey on 2007-06-29
I run utorrent under Wine on my Ubuntu desktop for my bittorrent downloads and recently, I lost the entire window GUI.

The application starts, and shows the icon up near the clock.  If i hover the mouse over it, I get stats (downloads/seeds) and right-clicking also gives me some options, but I cannot get the window to show up at all.

This happened after some issues with Compiz, which forced me to restart X (ctrl-alt-backspace) but all applications had been shut down before I logged out.

Has anybody seen anything like this with a wine-run app?  (an alcoholic application? :P )

I've only played with it a bit before I had to leave for work, so there may be things I've missed, or haven't checked out.

Edit:  The only other wine-run application I have installed is DVD Decoder, which still runs normally.


:cool: Eric the Grey

---

### Post by radinator on 2007-11-17
I just started having this happen tonight (Ubuntu 7.10 here).

I start up utorrent via wine either by clicking on the icon or invoking via the command line.  I can see in the process list that it is running, and I see from the system monitor that is has ethernet traffic coming and going, but I can't access the GUI by which to control it.  I just can't find it anywhere.

Any ideas?

Ray

EDIT:  Found the solution in another [thread]("http://ubuntuforums.org/showthread.php?t=486397&highlight=utorrent").  Thank you forums!  Deleting the uTorrent application folder in .wine did the trick.

---

