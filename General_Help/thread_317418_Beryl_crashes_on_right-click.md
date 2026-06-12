---
title: "Beryl crashes on right-click"
date: 2006-12-12
forum: General Help
---

### Post by dadutch on 2006-12-12
Hi everyone, since the second last version of Beryl I've come across an annoying problem with most Gnome applications (eg Totem, Gnome System Monitor, Firefox).

When I right-click on the titlebar emerald exits with a segfault. Also, right-clicking on any of these apps on the taskbar causes the application, Emerald and gnome-panel to crash. 

I'm currently running Ubuntu Edgy with the latest version of Beryl. Thanks for any input.

---

### Post by dadutch on 2006-12-12
Nobody? :(

---

### Post by PriceChild on 2006-12-12
I've noticed this a few times... I restart Beryl window manager via the beryl-manager tray icon and things sort themselves out.

---

### Post by mattds on 2006-12-12
It's a crappy answer, but I had the same problem until I restarted.  Just killing beryl and restarting gdm made no diff.

Best of luck.

M@

---

### Post by dadutch on 2006-12-12
Restarting the pc or the window manager itself doesn't work for me. The apps keep crashing.

---

### Post by jsteve54302 on 2006-12-14
Same here...  Restarting the Window Manager or rebooting brings back the window decorations, but right-clicking titlebars still crashes the window manager...  Thought it might be trailfocus doing something to the menu that crashed it, but turning that off did no good...  any other ideas?

---

### Post by jsteve54302 on 2006-12-14
OK, I <edit>**DID NOT find**</edit> a fix buried in another thread that was very long and had a cryptic title.  This <edit>**DID NOT**</edit> work for me, your mileage <edit>**will most definitely**</edit> vary:

<edit>Well, it did work, it seemed, for about ten minutes...  I right clicked on every titlebar I could get, and every one worked.  I posted this message.  I tested every titlebar again.  They worked.  I left my computer for five minutes.  I came back.  I right clicked on Firefox' titlebar.  Emerald Window Decorator crashed with a seg fault.  AAArrrghhhh!  Smeg!  Reeedmoooond!  I apologize for the confusion, all.</edit>

1. Open Emerald Themes Manager (right click on the red Beryl icon and choose the green stone :) )
2. Click on the Emerald Settings tab
3. Uncheck Button Fade Pulse
4. Close Emerald Themes Manager
5. Restart Computer (ok, reloading the theme manager should suffice, but I didn't do it that way, so I don't **know** that it will)

<snip>

---

### Post by Azakus on 2006-12-14
Do you run XGL or AIGLX? I used to have some similarly odd problems with XGL (no use of the "." key on the numpad, crash of X if I even looked at any options under nvidia-settings). If you can, try AIGLX.

---

### Post by jsteve54302 on 2006-12-14
> **Azakus said:**
> Do you run XGL or AIGLX? I used to have some similarly odd problems with XGL (no use of the "." key on the numpad, crash of X if I even looked at any options under nvidia-settings). If you can, try AIGLX.

I'm using the nVidia 9629 drivers, which (apparently) have AIGLX built in...  I didn't have to install/configure anything else to get Beryl working, at any rate, except the standard xorg.conf mods...

The only thing that keeps crashing is the window decorator, and I haven't had any other trouble.  Didn't have any 'til the last update, actually...  If it helps, here's a brief system config:

Abit AN8 32x mobo
AMD Athlon 64 X2 4800+
4GB Dual Channel RAM
EVGA GeForce 7950 GT KO 512MB GDDR3 (nVidia 9629 drivers)
Creative Sound Blaster Audigy 2 ZS Platinum
Ubuntu Edgy 6.10 Generic/Ubuntu Edgy 6.10 Generic/Win XP Triple boot

No, that's not a typo - I have one Ubuntu to keep stable for everyday use, one to "tweak" (read "repeatedly break and fix again" :) ) so I can get software installs right without mucking up my everyday work...  XP is just for games/IMVU...

Another thing I noted:  This time, Firefox, Nautilus, Gaim, StreamTuner, and all the Beryl/Emerald config windows had no right-click problem, but BOINC did...  last time, Gaim and Firefox made Emerald Decorator crash, but not BOINC...  I think Emerald's got a screw loose...

---

### Post by jsteve54302 on 2006-12-15
Update:

Some other odd behaviour I've just noticed:
1.  My kernel options in grub-gfxboot have suddenly changed to Debian, not Ubuntu, and my custom options (for booting my test bed) have disappeared (ie, something in the last updates overwrote menu.lst)...
2.  The last time I booted, I got this error from Gnome:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```dadutch, please forgive me for (sort of) hijacking this thread :), but this does seem to be the same problem, at least partly...

---

### Post by dadutch on 2006-12-15
No problem :D 

My problem is fixed by the latest beryl update. :cool:

---

### Post by jsteve54302 on 2006-12-15
Ah, still no joy...  I've even tried reinstalling everything related to beryl, and  disabling the plugins one at a time...  I did install the Beryl dbus plugin, and my last boot didn't generate a messagebus error, so maybe that's fixed now...  Although, yet another oddity - any window opened on startup by a saved session or by startup tasks has a sticky taskbar icon...  This may not all be related, but it did all start at the same time, and, well, Occam's Razor and all that...

---

### Post by Azakus on 2006-12-15
That sticky icon is theme controlled (my theme has one of those too). It's just more buttons really. You can disable that by changing what icons appear in the titlebar for your theme.

---

### Post by jsteve54302 on 2006-12-15
> **Azakus said:**
> That sticky icon is theme controlled (my theme has one of those too). It's just more buttons really. You can disable that by changing what icons appear in the titlebar for your theme.

Actually, I was talking about the taskbar icons...  It behaves as if I have set the "Show on all desktop" setting for those windows, except only the taskbar icon appears on all faces, not the actual window - clicking on the icon goes to the face the window is actually on.  The "Sticky" icon on the titlebar is off by default (the theme I'm using right now doesn't even have a pixmap defined for it - actually, it would be usefull if it did).  <edit> I'm providing info on the other problems in the hopes it will provide someone with the key bit of info to fix the problem. </edit>  However, this isn't my main problem...  I'm trying to get the Emerald Window Decorator to stop crashing semi-randomly  when I right-click windows' tiltlebars, a problem which didn't occur until the 1.3 upgrade  to Beryl.  The taskbar problem, and a couple others, started at the same time as the decorator-crash-on-titlebar-right-click, and don't happen at all if I use Metacity instead of Beryl, which suggests that the problems are somehow all related...  I'm going to purge the whole business and reinstall from scratch after Dr Who and see if that helps...  Good thing I've got the repositories defined in Synaptic...

---

### Post by jsteve54302 on 2006-12-15
Al right...  I think i've got it!  At least I'm getting menus instead of missing decorations for the moment :)  Here's what I did:

1.  Select Metacity as the Window Manager in Beryl, and close Beryl
2.  Use System Monitor to kill the emerald process.
3.  In Synaptic, search for Beryl, then Emerald, and selecting Complete Removal for all Beryl and Emerald packeges, and apply changes.
4.  Log out, press ctrl-f1 to get a virtual terminal.
5.  issue the command
```
sudo /etc/init.d/gdm stop
```6.  reinstall my video drivers (use the how-to you used to install yours the first time)
7.  Issue the command
```
sudo /etc/init.d/gdm start
```and log back in
8.  In Synaptic again, run the same searches, this time selecting Install for the packages I Completely Removed before.
9.  In a terminal, run the command
```
beryl-manager &
```Don't forget the '&', otherwise closing the terminal will also kill Beryl, and this could be bad.

Hope this really worked, unlike last time](*,) :)


Oh, and reinstalling the video drivers (steps 4-7) may not be necessary...  I just got paranoid.

---

### Post by jsteve54302 on 2006-12-15
Smeg it, I was wrong again!  This time the little bugger came back after a reboot...  I've tried reinstalling, purging and reinstalling, reinstalling video drivers, turning off all Beryl and Emerald Settings (no point in turning them back on one-by-one - it crashed with everything off)...  the only thing that gives me a reliable right-click is to just not use Beryl...  I really **like** Beryl...

Since I just can't get it to go away, I've submitted a bug report (this time it threw a seg fault at least)...  I'm also looking for the Beryl project bug report site...

---

### Post by jasidog on 2006-12-18
It may be to early to say this is a definitive fix. However after a bit of searching around this seems to have removed the issue for me.

I found a similar bug report at the beryl bug tracker thingydo - [http://bugs.beryl-project.org/ticket/132](http://bugs.beryl-project.org/ticket/132)

The suggested fix there for what seems like  a less wide spread problem than i myself have been experiencing. Is to downgrade libwnck "from 2.16.1-0ubuntu1.1 to the original coming from edgy (2.16.1-0ubuntu1)".

When I looked for it in synaptec I found libwnck-common and libwnck18. I forced both from 2.16.1-0ubuntu1.1 down to 2.16.1-0ubuntu1. Rebooted and things seem fine now. Though as noted in the bug report some or maybe many of the right click options have now disappeared. However crashes due to right click on title bar or the window's task bar button appear to have gone.

So you may find it worth a try.

---

### Post by jsteve54302 on 2006-12-18
> **jasidog said:**
> It may be to early to say this is a definitive fix. However after a bit of searching around this seems to have removed the issue for me.

I found a similar bug report at the beryl bug tracker thingydo - [http://bugs.beryl-project.org/ticket/132](http://bugs.beryl-project.org/ticket/132)

The suggested fix there for what seems like  a less wide spread problem than i myself have been experiencing. Is to downgrade libwnck "from 2.16.1-0ubuntu1.1 to the original coming from edgy (2.16.1-0ubuntu1)".

When I looked for it in synaptec I found libwnck-common and libwnck18. I forced both from 2.16.1-0ubuntu1.1 down to 2.16.1-0ubuntu1. Rebooted and things seem fine now. Though as noted in the bug report some or maybe many of the right click options have now disappeared. However crashes due to right click on title bar or the window's task bar button appear to have gone.

So you may find it worth a try.


Thanks for the reply... I just found this late last night.  It does fix the crashes, but as you said, it also removes some significant functionality (like the ability to send a window to another viewport), and a few windows still insist on being sticky (though this time they're truly sticky and can be unstuck).  The only way I've found to move  a window's viewport is to stick it, change cube faces, and unstick it...  bit of a kludge, but it works.  There was a diff patch for Beryl's screen.c and advice to download from Trevino's Beryl svn site if you don't want to compile Beryl yourself, but no instructions that would help a (mostly) non-programmer like me actually use the patch...  Hope the Beryl Project gets it into the repositories soon, because even if it only affects a few people, it's still a very serious problem for those people...

---

### Post by jasidog on 2006-12-18
Yeah it's certainly a bit debilitating but far better than what I had before. 

For some reason, I've not really looked into it yet likely something simple. New instances of windows always start out at the top left of the screen with the title bar hidden from view outside the screen. So this at least allows me to right-click on the taskbar button for that window to select move without it breaking.

The general problem only arose for me with beryl 0.1.3 so I can handle it until next update when with luck it will be fixed.

---

### Post by jsteve54302 on 2006-12-18
> **jasidog said:**
> Yeah it's certainly a bit debilitating but far better than what I had before. 

For some reason, I've not really looked into it yet likely something simple. New instances of windows always start out at the top left of the screen with the title bar hidden from view outside the screen. So this at least allows me to right-click on the taskbar button for that window to select move without it breaking.

The general problem only arose for me with beryl 0.1.3 so I can handle it until next update when with luck it will be fixed.


OK, I took another look at the patch... it's in workspace.c, not screen.c...  It's only two lines of code (not counting whitespace), and just sets a window's desktop to the current desktop if it's set 0xffffffff...  why anything would set it's desktop to such a ridiculous and unlikely number, I really don't know :).  I suspect desktop numbers are assigned sequentially starting at 0, and I doubt anybody has more than maybe 16 desktops...  And that with a multiheaded system...  At any rate, I don't see why a known and confirmed 2-line patch wouldn't make it into the next release, so I'll just wait for it... 

Cheers

---

### Post by jsteve54302 on 2007-01-11
The Beryl Project fixed this...  All's good now :).

---

### Post by d_fens on 2007-01-16
This occurs with me sometimes. Delete .recently_used (or of a similar name) in ~/

---

### Post by pjbgravely on 2007-01-20
Of course, the recent update that fixed peoples problems caused the same problems to happen to me. Maybe if I revert I can use beryl again.

Paul

---

