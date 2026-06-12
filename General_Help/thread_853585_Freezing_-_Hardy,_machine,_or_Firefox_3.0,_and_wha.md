---
title: "Freezing - Hardy, machine, or Firefox 3.0, and what to do"
date: 2008-07-08
forum: General Help
---

### Post by 5circles on 2008-07-08
I'm running Hardy on a new machine that hasn't had much use, so I have no idea what's causing the problems.

Every so often Firefox will lock up.  The screen goes gray with the site still visible.

I hoped I might get to a Ubuntu equivalent of Windows Task Manager with <Control><Alt>Delete.  No such luck - just a set of shutdown options.  I finally figured out I should have been looking for System monitor, but haven't seen the problem since.  I tried following the instructions in [http://ubuntuforums.org/archive/index.php/t-331065.html](http://ubuntuforums.org/archive/index.php/t-331065.html) to set key bindings, but it seems that the existing <Control><Alt>Delete setting has priority.  No big deal - I set up <Control><Alt>End to point to System Monitor instead.  So hopefully I'm set for next time.

But, does anyone know if this is a Firefox 3.0 problem?  This is the only machine I'm running 3.0 on.

Or is it likely to be a Hardy problem, or a graphics problem?  And how do I tell?

Thanks
Mike

---

### Post by Het Irv on 2008-07-08
If you can still use the mouse, you can click the close button and it will ask you if you want to force quit.

As to the FF3 problem, what was your browser doing right before the crash?

---

### Post by kevinatkins on 2008-07-08
I had quite a few problems with Firefox 3 freezing with a fresh 8.04 install, with the (then) FF3 beta, but subsequent updates have fixed Firefox. Is your machine right up-to-date with updates?

In cases where programs have crashed, I've found it very useful to have the 'force quit' applet installed on one of my panels - just right-click on either the top or bottom panel, select 'add to panel' and choose the 'force quit' applet. Then next time an app misbehaves, click on 'force quit', move the mouse over the dead application and click - voila, the app is terminated...

---

### Post by 5circles on 2008-07-08
Thanks for the suggestions.

1.  I'm not sure if I was able to click on the close button or if I wasn't patient enough.  I'm so used to Firefox / Ubuntu being stable that I didn't initially pay enough attention.  

2.  Last FF3 action was - I think - trying to go to a new link.  It might have been ALT leftarrow.  Again, I'll be watching more closely.

3.  I think everything is up-to-date, including the release version of Firefox.  The kernel update threw me because it undid my patch for the Realtek network card, but it is working again (and I'll be watching for kernel updates in future - hopefully the Realtek driver will be fixed soon).

4.  Good tip on the Force Close applet.  I just spent a few minutes learning about the panels.

---

### Post by noworry on 2008-07-22
I am also having this black-out (greying) very frequently and it is really annoying.

I have been using hardy since its release, but this freeze problem started happening recently in firefox 3 as well as thunderbird. 

Currently only option is to force quit. I don't know of any way to debug this since it doesn't produce any crash report. Could anybody help me in debugging and solving this issue?

This is really a high priority for me !!

---

### Post by noworry on 2008-07-22
I just installed firefox 3.0.1 from hardy-proposed. Let me how it goes and I ll post the result

---

### Post by Spainface on 2008-07-25
I'm also getting frequent 'grey-outs' in FF3.  It tends to happen with things like 'poke' on facebook (yes I know I shouldn't be on it anyway) and videos on sites like the BBC.  It tends to go away after about 30 seconds.  Tres annoying.  I use the NoScript add-on, if that factors in.

Oh ya, and a window opens on the taskbar called npviewer.bin

Thanks,

---

### Post by noworry on 2008-07-26
upgrading to firefox 3.0.1 doesn't solve the problem, it still freezes lot of times, very annoying.

I think it may be a bug in ubuntu !!

---

### Post by MicahCarrick on 2008-07-29
I waited until now to upgrade to FF 3... same problem. Even with all extensions disabled, cache cleared, etc. Ajax/multimedia heavy sites cause periodic freezes to the whole system, not just the browser. I have AMD64 dual core with 4GB RAM and it's still a significant freeze, typically lasting about 3 seconds several times in a row for any of these pages.

I'm seeing this problem a lot in forums and blogs (Windows and Linux) but have not found any answers that work.

---

### Post by Het Irv on 2008-07-29
If you run Firefox from the terminal, do you get any usefull information on the freezes?  Is there anything in the logs?  Its insane hard to debug if you can't find the problem.

---

### Post by tas_mania on 2008-08-03
Total lock-ups with X-Windows freezing on an otherwise stable machine. (Hardy and Firefox 3.0.1) Only pages with Adobe Flash content seem to cause this problem. I'm thinking of rolling-back to an earlier Firefox.
Cheers.

---

### Post by 3rods on 2008-08-03
Are all of you running 32-bit? 

I've had similar issues with 64-bit and more recently with pages that have lots of flash in 32-bit (i.e. youtube). I believe I reinstalled flash (restricted, not gnash) to get it working again.

---

### Post by tas_mania on 2008-08-05
Thanks 3rods for the clue. No it doesn't look like flash is my problem.
Running 32 bit system

---

### Post by linux_tech on 2008-08-05
[http://kb.mozillazine.org/Standard_diagnostic_(Firefox](http://kb.mozillazine.org/Standard_diagnostic_(Firefox))

---

### Post by tas_mania on 2008-08-07
Is Firefox 3.0.1 freezing on this webpage?

[http://www.hackaday.com]("http://www.hackaday.com")

THE PROBLEM IS NOT FIREFOX IT'S THE ATI 8.6 DRIVERS.
I uninstalled the older ATI driver and the above page works.
It just looks like a Firefox problem because that was running when the x-server crashed.
I upgraded to the 8.7 ATI Radeon drivers and now its all OK.
I followed these instructions:
[http://ubuntuforums.org/showthread.php?t=866495]("http://ubuntuforums.org/showthread.php?t=866495")

---

### Post by noworry on 2008-08-08
Got some useful debug info by running firefox in the terminal.

The following error message keeps on coming in the terminal during the freeze

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket

After which the browser becomes unusable until I force quit and restart. During force quit, I got this error (may be irrelevant)

(firefox:12586): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


The interesting thing is that, even after i force quit the firefox, the error message "DCOPClient::attachInternal. Attach failed Could not open network socket" keeps on coming in the terminal !!!

So, looks like a ubuntu bug, not sure. 

Could somebody please help me in fixing this issue? This is really driving me crazy.

---

### Post by noworry on 2008-08-09
Searched for the error and found that "dcopserver" crash is the cause and running it solves the problem. Don't know how it is crashing on visiting some web pages.

---

### Post by Kain000 on 2008-08-09
> **Spainface said:**
> I'm also getting frequent 'grey-outs' in FF3.  It tends to happen with things like 'poke' on facebook (yes I know I shouldn't be on it anyway) and videos on sites like the BBC.  It tends to go away after about 30 seconds.  Tres annoying.  I use the NoScript add-on, if that factors in.

Oh ya, and a window opens on the taskbar called npviewer.bin

Thanks,

I dont think no script is the problem, because I have the same problem without it.    However I believe it could contrbuite to it, It goes grey (at least in my experiences) when transfering a large ammount of data between a server and my laptop such as a video, witch leads me to believe that the problem lies with the fact that FF3 uses alot of memory, and could perhaps be locking up due to a timeout issue because it doesnt freeze, just keeps you from doing anything for a bit while it works on what it already has.
just a thought.

---

