---
title: "System Hangs on Startup, garbage on screen..."
date: 2007-11-24
forum: General Help
---

### Post by secretspicy15 on 2007-11-24
Ok, I have no idea what is going on with my computer. Night before last it was working fine, no symptoms of anything wrong at all. I didn't make any major changes, I wasn't fiddling with dangerous system files or doing excessive configuration. I woke up yesterday morning and the screen was blank. The monitor backlight was on, but the screen blank. At first I thought maybe it was in some form of suspension for some reason, but nothing would wake it up. I then tried alt-cntrl-backspace (and alt-ctrl-del, out of old habit) and nothing happened. I eventually powered it down via the hardware switch, waited a while, and turned it back on. Nothing. I eventually figured out that my LCD for some reason was just not displaying anything(after hearing the drum for the login screen once), so I got an external monitor and connected it.

With the external monitor when I power up the system I get to grub (I dual boot Edgy and Winxp), but there's weird garbage across the screen... like little squiggles here and there; I've never seen anything like it (well, maybe a nintendo game that won't load up and needs to be cleaned...)... I then select ubuntu, it shows the ubuntu logo with scrollbar, loads up, switches to a blank screen with a flashing cursor in the top left and that same squiggly garbage across the screen, sits there for a little while, then everything goes blank.

I have tried alt-ctrl-F* ing while the system is loading -- it just sends me straight to the flashing cursor with garbage.

I have tried booting into windows even -- it displays the windows logo and pseudo progress bar, then blanks out on me.

When I try booting into recovery mode for Ubuntu, it says loading nn (with garbage all over the screen) and hangs there indefinitely -- I walked away and left it for hours yesterday and it was still like this... Every time I have to resort to manually powering off.

I have not tried a live cd yet; I am currently at my Mom's and don't have onewith me; the infrarecorder download is down, which is preventing me from burning a new one from iso here, but I have one at home to try tomorrow.

The only thing I could successfully do is get to the grub command line (not very useful to me; I don't know how to do much of anything there...) or run the Memtest... I am actually kind of confused as to what the memtest does, however, It took ages for it to make one pass and then it seemed to be doing the same thing again -- does it do this indefinitely, or does it finish at some point? I ended up hitting esc to reboot. Throughout the memtest there was garbage across the screen as well.

If anyone has any ideas whatsoever, it would be very much appreciated. If nothing else, hopefully I will be able to get the live cd to work, and will be able to access my hard drive from there, back up everything (I swear i will become a regular back-upper after this...)and reinstall ubuntu -- the upswing of this is that it would be an opportunity to get rid of windows for good :-D

Thank you in advance!
TJ

---

### Post by dcstar on 2007-11-24
> **secretspicy15 said:**
> 
...........
If anyone has any ideas whatsoever, it would be very much appreciated. If nothing else, hopefully I will be able to get the live cd to work, and will be able to access my hard drive from there, back up everything (I swear i will become a regular back-upper after this...)and reinstall ubuntu -- the upswing of this is that it would be an opportunity to get rid of windows for good :-D

Thank you in advance!
TJ

Sometimes powering off or rebooting a modern PC does not actually fully power off the motherboard - which you sometimes need to do to fully reset all the hardware when weird things start happening.

Try pulling the power cable out of the back for a minute or so, and then put it back and see if things have changed.

---

### Post by secretspicy15 on 2007-11-25
It's a laptop -- I did turn it off and remove the battery for a while, without much success.

---

### Post by secretspicy15 on 2007-11-25
Ok, well I found an old livecd, which I am running right now, and it is working (obviously; this is where I am writing from) I have mounted my hard drive and can see all of my contents, however it seems tantalizingly just out of reach -- I cannot copy anything over to my usb drive! I don't know why, it doesn't give any error messages or anything -- I drag a folder or file to the usb and nothing happens. I try copying and pasting, nothing happens... I can't even see the files through gmail to try and send them to myself... this sucks. lol...

If anyone has any ideas, that would be fantastic... At this point I just want to get valuable data and pictures etc off of this beast so that I can start anew... please help!! :'(

---

### Post by secretspicy15 on 2007-11-25
Ok, some progress at this point -- I found that I could create archives of my data, and then do with those what I pleased. So now all of my important files are safe and away from this computer, and I have a gutsy live cd running in safe graphics mode....

I still need to use my external monitor though...

Is it possible that I destroyed my graphics card somehow? It seems my LCD that is built in to the computer is connected still, because it lights up when it should, it just does not display anything... The CRT I have connected right now works fine in safe graphics mode, but when I tried to boot into the normal livecd, it would give me very corrupted graphics (looks like when you connect a monitor of the incorrect resolution) , then clean up a bit, but hang and delay in screen refreshes, and eventually lock up.

And, as I stated before, the garbage all over the screen anytime it is in console-type display. Any ideas?

---

### Post by secretspicy15 on 2007-12-28
Ok, all is resolved! :-D it was the graphics card that was bad; I finally contacted dell support and the replaced it under warrenty.

Thank goodness.. that was a mess...

---

