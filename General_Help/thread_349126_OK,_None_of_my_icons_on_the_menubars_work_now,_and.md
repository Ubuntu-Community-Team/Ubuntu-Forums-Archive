---
title: "OK, None of my icons on the menubars work now, and other menu items &quot;time out&quot;!"
date: 2007-01-29
forum: General Help
---

### Post by emarkay on 2007-01-29
Help!

I can't get to terminal, there's no way to exit Ubuntu, and looks like this browser is the only thing working!  Open Office, Gaim, they all just time out!  

I did notice that my shutdown button did open up before I restarted, but only the top 3 and the single "hibernate" button appeared.  (I logged out and shut town at teh log in screen to restart).

I'll leave this up (what else can I do?) and hope someone has some suggestions.  (!)

---

### Post by meng on 2007-01-29
Try
alt-f2
gnome-terminal

to get to the terminal. Then try initiating other applications from the terminal to see what happens.

---

### Post by emarkay on 2007-01-29
I get that application menu and it says "will run command '/usr/bin/gnome-terminal' and I hit run and nothing happens but the whole application menu just immediately disappears.

This is WEIRD!

---

### Post by emarkay on 2007-01-29
I remember an "About Ubuntu" item near "About GNOME" under the system menu, but it's missing now if that is a clue...
Even the 'QUIT" menu item under System does nothing!

---

### Post by emarkay on 2007-01-29
I can't even get to my "home folder" !

---

### Post by meng on 2007-01-29
So you're saying alt-f2 doesn't work huh? Did you change anything on your system recently?

---

### Post by emarkay on 2007-01-29
I was looking at what thumbnails were by using System configuration - see this thread:

[http://ubuntuforums.org/showthread.php?t=348510](http://ubuntuforums.org/showthread.php?t=348510)

As I recall that was it - I wanted to get into terminal to GKSUDO NAUTILUS delete a plugin file on my browser root, but that is when I noticed Terminal would not open! 

What could be causing this???

---

### Post by emarkay on 2007-01-29
> **meng said:**
> So you're saying alt-f2 doesn't work huh? Did you change anything on your system recently?

Alt f2 gives me the "application menu" - I look for Gnome Terminal, and click on it.  It then says "will run command '/usr/bin/gnome-terminal' and I hit run.  Nothing happens and the whole application menu just immediately disappears.

---

### Post by emarkay on 2007-01-29
All the mouseovers work, but clicking on the icons puts up the clock type hourglass thing and the "starting application" note in teh lower tool bar for about 5 seconds than it all goes back to wher it was before I clicked - nothing.

---

### Post by mayonaise15 on 2007-01-29
Try Ctrl-Atl-F2 to get to TTY 2
Ctrl-Alt-F7 gets you back to gnome.

---

### Post by emarkay on 2007-01-29
> **mayonaise15 said:**
> Try Ctrl-Atl-F2 to get to TTY 2
Ctrl-Alt-F7 gets you back to gnome.

OK that works.
But I am a but behind on my "running Ubuntu in terminal mode only".

Maybe someone can give me some diagnostics or something - I really don't want to have to reload and download 150MB worth of updates plus all the Automatix updates again!  :(

And yes, I restarted recently and I am still having the same problems in the "GOOEY" mode!

---

### Post by emarkay on 2007-01-29
Anyone?  :)

---

### Post by emarkay on 2007-01-29
I found 15 other posters her with a similar problem - (I excluded the NVIDIA and "beerorchid' (I think it is) issues) and NO ONE has a solution.  Of course, some of the posters reported that things 'suddenly" worked again, but many just whimpered away unanswered.

Pretty lame I would say that people are having this problem and no one seems to even want to diagnose it to solve what may be a bug in Ubuntu.

I am frustrated, and am just going to power off this PC (The only way I can now exit Ubuntu) and HOPE that someone takes this seriously and provides some feedback

BTW, the post links:
[http://ubuntuforums.org/showthread.php?t=345109&highlight=terminal](http://ubuntuforums.org/showthread.php?t=345109&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=339608&highlight=terminal](http://ubuntuforums.org/showthread.php?t=339608&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=336925&highlight=terminal](http://ubuntuforums.org/showthread.php?t=336925&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=323553&highlight=terminal](http://ubuntuforums.org/showthread.php?t=323553&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=322091&highlight=terminal](http://ubuntuforums.org/showthread.php?t=322091&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=309423&highlight=terminal](http://ubuntuforums.org/showthread.php?t=309423&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=308056&highlight=terminal](http://ubuntuforums.org/showthread.php?t=308056&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=306130&highlight=terminal](http://ubuntuforums.org/showthread.php?t=306130&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=298605&highlight=terminal](http://ubuntuforums.org/showthread.php?t=298605&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=297640&highlight=terminal](http://ubuntuforums.org/showthread.php?t=297640&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=295745&highlight=terminal](http://ubuntuforums.org/showthread.php?t=295745&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=293294&highlight=terminal](http://ubuntuforums.org/showthread.php?t=293294&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=285250&highlight=terminal](http://ubuntuforums.org/showthread.php?t=285250&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=286393&highlight=terminal](http://ubuntuforums.org/showthread.php?t=286393&highlight=terminal)
[http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal](http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal)

And these are  JUST those with terminal probs like mine - what about Exit, and screen snapshot, and notepad and all the System Applications and everything else that is trashed...

AAAARRRGGGHHH!

---

### Post by irish_flu on 2007-01-29
Well for starters, I don't know what's causing your problem.  That said, I'll try to offer suggestions.

Have you tried reinstalling Gnome (assuming that's what you're using), perhaps using Synaptic to mark the ubuntu-desktop package for reinstallation?

It might be overkill, but it might fix your problem too.

An aside: Don't worry so much, my fellow southern-Hoosier.  Waiting two hours for somebody to answer your question on a community message board for a free operating system isn't something to get all worked up over (and start cross-posting agitated threads).  :D


BTW I live between Bloomington and Bedford.  Glad to see I'm not the only Ubuntu user this side of I-70!  :)

---

### Post by Sunflower1970 on 2007-01-29
I don't know what's going on with your icons, but I did have a problem with my terminal opening and closing again really quickly. I had discovered I had somehow logged in as the root user. Once I was able to log out and log back in as me, everything was perfectly fine. 

I did have a problem with my icons not long ago...my whole desktop crashed after I had installed a theme. Turns out I had done something kind of silly. :oops: I had chmodded the folder where the particular theme was to be read only (I think I made it read only...but whatever I did wasn't good), and everything pretty much was unusable. And why I did it, I really don't remember the reason except I thought it was a great idea at the time--caused me to have to reinstall everything because I couldn't figure out how to fix the problem...

---

### Post by emarkay on 2007-01-30
> **irish_flu said:**
> An aside: Don't worry so much, my fellow southern-Hoosier.  Waiting two hours for somebody to answer your question on a community message board for a free operating system isn't something to get all worked up over (and start cross-posting agitated threads).  :D  BTW I live between Bloomington and Bedford.  Glad to see I'm not the only Ubuntu user this side of I-70!  :)

Thanks, and to others! 

I am documenting this for my reference - I am going to reinstall Ubuntu.
I re-instaled this PC's Ubuntu  in October, and it was one of my first "Ubuntus".  I may have some "upsidedown pyramids" here (ya' know like windows, put things in, delete them, test this, reconfigure that, blah blah blah, and one day you get the BSOD - or in this case, nothing works but the browser...)
Thanks for the time to think, and I do hope that others with this problem find a solution that does not take 3 hours -(a reinstall and redownload of all updates...)  :)

Will post later if all goes well to close this thread.

MRK

PS: Irish Flu - The Evansville LUG is dead, and the  KY and OH LoCo's are pretty far away to make a periodic evening "face-to-face", and the activity is all Bloomington and north in IN.  We need something in the Jasper, Washington, Princeton,  Evansville, Owensboro, Salem locations...  Any ideas?

---

### Post by Joe Sixpack on 2007-01-30
Seems like I am having the same issue.  What I have to add is that it happened while I was working.  One minute file browser worked fine, then later on it didn't.  The only thing I did in between was install a couple of the automatic updates.  I wish I could remember the package names right now, but I can't.  I didn't mess with it enough last night to see all of these symptoms.  What I noticed was that when I click "Places" and "Home Folder", I get the hourglass, and there is a 'starting home folder' button on the taskbar.  After 5 seconds or so it disappears, never displaying the home folder.  Same thing for any file browser window I try to open, at least through the 'places' menu.  Hope it helps.

---

### Post by irish_flu on 2007-01-30
> **emarkay said:**
> 
PS: Irish Flu - The Evansville LUG is dead, and the  KY and OH LoCo's are pretty far away to make a periodic evening "face-to-face", and the activity is all Bloomington and north in IN.  We need something in the Jasper, Washington, Princeton,  Evansville, Owensboro, Salem locations...  Any ideas?

Not much activity in Bloomington either, unfortunately.  The University has several active folks, but not much going on outside of it.

---

### Post by Joe Sixpack on 2007-01-30
emarkay - 
On the last link you posted, the person had a fix.  Have you tried that yet?
[http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal](http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal)

---

### Post by emarkay on 2007-01-31
> **Joe Sixpack said:**
> emarkay - 
On the last link you posted, the person had a fix.  Have you tried that yet?
[http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal](http://ubuntuforums.org/showthread.php?t=244787&highlight=terminal)

It was posted after time ran out - I'll mark this thread resolved, and see the other one for my show of appreciation later today - I did a step-by-step list of reinstalling and configuring of a typical Ubuntu for easy reference I'll make available.

Thanks!

---

### Post by emarkay on 2007-02-01
Here's the guide, and I'll mark this "resolved"

[http://ubuntuforums.org/showthread.php?p=2092150#post2092150](http://ubuntuforums.org/showthread.php?p=2092150#post2092150)

---

