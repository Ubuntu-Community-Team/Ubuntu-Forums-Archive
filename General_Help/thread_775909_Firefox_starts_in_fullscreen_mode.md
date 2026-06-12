---
title: "Firefox starts in fullscreen mode"
date: 2008-04-30
forum: General Help
---

### Post by aheckler on 2008-04-30
Sometimes when I start Firefox it starts in full screen mode, with the title bar not visible and the status bar covering up my panel at the bottom of the screen. I have to press F11 or something to get it to revert to the regular maximized mode. Has anyone else been experiencing this?

I just started having this problem this morning, and I know there were a few updates so maybe it was something in there that's causing the problem?

---

### Post by psychofish25 on 2008-05-16
(bump) im having the same problem. can someone please answer?

---

### Post by strabes on 2008-05-16
If you create a new firefox profile by running ```
firefox -ProfileManager
``` is the problem fixed? If so, then just use that profile and reinstall your addons, etc. Probably not the solution you were looking for but it may do the job.

---

### Post by Mozork on 2008-08-05
It works, but that's not the solution I was looking for, because I would loose my history, add-on preferences, a.s.o.

So I would be grateful for other solutions. :D

---

### Post by Mozork on 2008-08-05
Alright... I've been trying some things and the problem is somewhere in the localstore.rdf file, so by creating a new firefox profile, and copying the localstore.rdf file from that profile to your regular profile should make the problem go away. 

The localstore.rdf file stores the size and position of many different firefox windows, so that they are in the same place you left them last. Also it stores the makeup of the browser, that means, if you've changed some buttons, you'll havbe to do that again. Apart form that you should lose nothing.

---

### Post by expletivization on 2008-10-19
I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

---

### Post by ju2wheels on 2008-10-19
Its definitely a bug in 3.0.3 thats quite random, but its not really going fullscreen. Its actually just opening maximized and not realizing the top panel is there so it extends too far up and is redrawn under the top panel. So resizing the window and remaximizing is the only way to get the title bar back at the right height.

---

### Post by dixon1960 on 2008-10-26
I think I'm seeing the same problem. The way it manifests itself is this. I use an external monitor (1680x1280) with my IBM x61 laptop. Sometimes, (often) I leave the browser window bigger than 1024x768 (the laptop display size) when I shut down. If I then disconnect the monitor, reboot the browser using the laptop monitor, and start firefox it starts maximized. I can see the browser file menu at the very top of the display, I can see the browser status bar at the bottom. Unfortunately I can't see see the Ubuntu menu at the top or Ubuntu bar at the bottom. The only keyboard short cut that works is Alt+F4 to minimize the browser window. I can't resize the browser Window, move it or do anything with it.
Same problem? Advice?
Thanks, Colin.

---

### Post by Flecko on 2008-10-27
I'm having the same problem. Taking firefox out of maximized mode, then remaximizing, and closing/reopening seems to have fixed the problem...but man...this should be addressed.

My wife was having the same issue, and it was going on for like 2 days...she wouldn't know how to fix it without me. 

Does anyone know if there is a Launchpad bug for this yet?

---

### Post by arglborps on 2008-10-27
Same issue here and expletivizations solution worked. Thanks a lot. This really drove me crazy.

---

### Post by fooman on 2008-10-27
> **Flecko said:**
> 

Does anyone know if there is a Launchpad bug for this yet?

launchpad bug with same fix as above:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400)

---

### Post by Flecko on 2008-10-27
Thanks fooman.

I hope they get this fixed before Intrepid ships.

---

### Post by Krieg on 2008-10-31
I got the same problem, pretty annoying.   I fixed by changing browser.fullscreen.autohide to false in about:config

---

### Post by hesjnet on 2008-11-06
> **expletivization said:**
> i was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!


thanks! :ks

---

### Post by neu2buntu on 2008-11-07
just had the same prob ,..expletiv,s method worked for me (resize can be found by right clicking on the panel window, after pressing f11 twice)... must be a bug of some kind...seems to be affecting a lot of ubuntuers:lolflag:

---

### Post by sirebral on 2008-11-07
FIX::

Got to the .mozilla/firefox folder in your Home directory and delete the localstore.rdf file.

---

### Post by Kprojekt on 2008-11-08
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!


This worked for me, Thanks Expletivization!

---

### Post by commonplace on 2008-11-08
Same problem, just started happening today after I rebooted. expletivization's fix worked for me -- thanks!

/Kevin

---

### Post by 73ckn797 on 2008-11-09
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!


That is what I like. A simple, non CLI fix. Thanks!

---

### Post by billgoldberg on 2008-11-12
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

Yeah, that did the trick.

I had been having this problem for a week or so now, I knew I could just use a new profile, but was to lazy to do so.

Thanks.

(is this compiz fusion related?)

---

### Post by irish66 on 2008-11-17
Hi.
This is not just happening on me in Firefox, but in other programs too
ie when i open a program such as Firefox, the only way to see the file menu is to unmaximise, and then move.
I've tried the resizing tip, but didn't work, even after rebooting.
It's also happenning in programs such as Krusader, and Peerweb (emulated with Wine)       
Well I guess that's one advantage, that windows has. Usually you can tell a program not to run maximised through the properties menu.
couldn't try local store method, as told, i don't have permission to do anything with that file. 
okay. i have to create a new profile. Is that just a new text file? 
M

---

### Post by mitch_feaster on 2008-11-28
Same problem here with Intrepid and Firefox 3.0.4.  Fixed with sirebral's fix:

> **sirebral said:**
> FIX::

Got to the .mozilla/firefox folder in your Home directory and delete the localstore.rdf file.

(note that you must do this while firefox isn't running for it to work because it writes that file on exit!)

---

### Post by luckyspot on 2008-12-07
> **sirebral said:**
> FIX::

Got to the .mozilla/firefox folder in your Home directory and delete the localstore.rdf file.

thank you. i started having this problem today and sirebral's method worked!! p.s.: you first need to close your browser before performing the operation

---

### Post by shatteredmindofbob on 2008-12-11
"Legacy Fullscreen Support" under Workarounds in Compiz Fusion seems to be the problem. I disabled it and the bug is gone, but now Firefox is painfully slow for some reason...

It also doesn't make much sense that this is something that would just suddenly happen. Wouldn't something have to happen to trigger the problem in the first place?

---

### Post by addiebk on 2008-12-18
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

This worked perfectly for me!  Thanks!  It was really starting to get on my nerves. :D

---

### Post by eode on 2009-01-29
To fix this more permanently (It kept recurring, for me, even after getting firefox to the right size, then closing it so that it saves settings), I turned off Legacy Fullscreen Support in Compiz.

To do this:

[LIST=1]
[*]Install *CompizConfig Settings Manager*
[LIST=1]
[*]Go to Applications->Add/Remove
[*]Search for "compiz"
[*]Install "Advanced Desktop Effects Settings (ccsm)"
[/LIST]
[*]Turn off Legacy Fullscreen Support in CompizConfig Settings Manager
[LIST=1]
[*]Go to System->Preferences->CompizConfig Settings Manager
[*]Click on "Advanced Search", near the bottom left.
[*]In the "Filter" box, type in "Legacy"
[*]Click on "Workarounds" in the "Plugin" box.
[*]In the box below, uncheck "Legacy Fullscreen Support"
[*]Close the Settings Manager.
[/LIST]
[/LIST]

Thanks for your tip about this, shatteredmindofbob.

---

### Post by Gcottrell on 2009-02-04
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

That is the correct answer,. it worked for mine flawlessly. Thank you!

---

### Post by freesitebuilder on 2009-02-05
> **Krieg said:**
> I got the same problem, pretty annoying.   I fixed by changing browser.fullscreen.autohide to false in about:config

I got this problem suddenly this week - probably because I've changed my monitor and updated my graphics card driver. Couldn't resize as the window was too tall and I couldn't get to the corners.

Tried this solution, and it made it worse. So I restarted Fx, and changed it back. That's cured it. Totally illogical - but I'm happy not to understand, just to enjoy. ;)

---

### Post by iansyngin on 2009-02-11
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

This solution worked for me also.
I think my problem manifested itself because i had enabled my top panel to Autohide. When it did autohide, firefox also increase in height. Then when i turned off autohiding firefox remains this bigger size. Just wanted to throw my 2 cents in.

---

### Post by Kerel on 2009-02-13
> **expletivization said:**
> I was having this problem too and figured out a goofy way of fixing it (at least it worked on mine) without changing profiles or anything.

After firefox starts up in annoying fullscreen mode, take it out of fullscreen, and un-maximize the window.  Resize the window to something smaller (mine was too tall), and then remaximize.  Close and restart firefox.

Voila!

Thx, I've been looking into this for days, because it's my brother's pc and I thought he just changed something o_O. 

It's a logical bug, but it sucks...

---

### Post by wouitmil on 2009-02-24
expletivization's solution was perfect for me.

Tks!

---

### Post by Obfuscator on 2009-03-03
expletivization's solution worked for me too. I think that this bug occured to me after miniFox was disabled after a ff update, hence the window got "bigger" with all full size decorations of the default theme.

---

### Post by mynk on 2009-04-27
I had the same problem with an external screen. Resizing has helped. Till then I was using F11 to get into full screen mode and then back to maximized screen. This was obviously not helping. Look forward to a proper fix.

---

### Post by GetMeAWrapCombo on 2010-09-28
Not to necrobump, but for other readers, this issue is NOT compiz or ubuntu related. It has appeared for me in Xmonad in Arch Linux. It appears to be an issue with firefox settings. It seems to appear when firefox is closed while fullscreened. 

The easiest known fix is to unmaximise your window, resize it, maximise (not fullscreen) then restart firefox.

If your window is too large for your screen, try dragging your firefox window with alt-leftclick and drag anywhere in the firefox window (you all knew you could do this with any program in linux, right?) and go from there.

---

### Post by nryc on 2010-12-25
> **GetMeAWrapCombo said:**
> Not to necrobump, but for other readers, this issue is NOT compiz or ubuntu related. It has appeared for me in Xmonad in Arch Linux. It appears to be an issue with firefox settings. It seems to appear when firefox is closed while fullscreened. 

The easiest known fix is to unmaximise your window, resize it, maximise (not fullscreen) then restart firefox.

I confirm, I've deleted all compiz-* packages and the problem is still there so it's not compiz-related. Just to make sure : it is impossible to start firefox in "real" full screen, it starts with the regular toolbar and menu items.

Deleting the "localstore.rdf" file from the firefox profile doesn't work either, it just resets the window placement.

---

