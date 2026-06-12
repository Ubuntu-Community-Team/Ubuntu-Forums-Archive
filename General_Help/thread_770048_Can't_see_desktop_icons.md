---
title: "Can't see desktop icons"
date: 2008-04-27
forum: General Help
---

### Post by spliffeh on 2008-04-27
I recently messed around with Compiz Fusion and Nautilus settings (I was trying to get different wallpapers on all 4 sides of my cube desktop).

As a result I no longer have any icons on my desktop, and if I right click the desktop nothing happens.

Can anyone tell me how to show desktop icons again?

---

### Post by Bubba64 on 2008-04-27
If you go to the top of the screen and right click new panel then right click on the panel then add to you can hopefully restore the original menus etc. Do the same on the bottom of the screen.

---

### Post by spliffeh on 2008-04-27
I think you misunderstood my question Bubba64
My two menu bars are fine, upper and lower.

The problem I have is no icons on the desktop itself.
Also, I cannot drag & drop files onto my desktop, or right click it, etc.

---

### Post by bn127 on 2008-04-27
Try this:

With ALT+F2 open gconf-editor, then in _apps>nautilus>preferences_ tick _show desktop_

bn127

---

### Post by the.original.kermit on 2008-05-18
I am also having this exact issue, mine happened the same way.  I'm not sure what it is, did anyone figure this out?

---

### Post by the.original.kermit on 2008-05-18
Ok, fixed the problem.

The box was already check, but it still wasn't working.  Unchecking then rechecking the box fixed the issue.

---

### Post by astadolfo3 on 2008-07-11
I used the solution above by unchecking-chekhing the show desktop box. The icons appeared however after I reboot they disappear again. The check box is always checked, but I have to uncheck-recheck everytime I reboot. What is happening? If normally is already checked, why don't the icons show?

---

### Post by WhyZeeGuy on 2008-11-23
I'm experiencing the same issue.  

I had only the Trash icon on my desktop (I roll like that :cool:) and was playing around with the desktop wallpapers in Compiz.  I couldn't get the wallpapers to work they way I wanted them to, resolution/scaling issues so I changed the settings back using gconf-editor apps>nautilus>preferences> Show Desktop and apps>nautilus>desktop Show Trash but the trash icon was not restored to the desktop. Also, I have no left click functionality on the desktop and cannot view any files sent to the desktop.  Checking and un-checking the options produces zero results.

I'm running 8.04 Hardy 

Any help is greatly appreciated.

---

### Post by PilotJLR on 2008-11-30
I have the exact same issue... haven't figured it out yet, and gconf-editor isn't resolving the problem.

Running 8.10 Intrepid on AMD64.

For the time being, I've found that I can fix the problem by logging out and then logging back in.

---

### Post by JEdwardP on 2009-01-02
My issue isn't the same, but it does cause all my desktop icons to disappear. I don't know if it's a Gnome bug our a mount bug, but for the last couple days, whenever I turn on any external USB drive or insert my USB flash drive, my desktop icons blink two or three times, three windows titled "starting file browser" attempt to launch, and then finally all my desktop icons disappear, and I lose all right-click menu functionality on the desktop (the context menu will no longer appears).

Rebooting always fixes this, but it's highly annoying, and ANY help would be greatly appreciated. I'm running 64-bit Intrepid.

---

### Post by hansdown on 2009-01-03
Hi JEdwardP.

This should help.

[http://techbycolin.com/?p=129](http://techbycolin.com/?p=129)

---

### Post by JEdwardP on 2009-01-11
Thanks Hansdown,

But this phenomenon amounts to a desktop crash; using gconf to uncheck and recheck the icons has no effect.

Not only to my desktop icons disappear, but the desktop's context menu will no longer appear upon right-clicking. ctrl-alt-backspace or a full reboot always resets things, but the behavior recurs each time I turn on an external USB drive..

I searched Launchpad with a string like "USB desktop crash" to see if I could find a known bug that covers this, but had no luck. The most curious thing is that this behavior only began about a week ago, and I've made no hardware changes to either of my machines (both run 64-bit intrepid) during that time.

---

### Post by hansdown on 2009-01-11
Hi JEdwardP.


There is an ongoing thread with similarities to this one. It's quite long.

[http://ubuntuforums.org/showthread.php?t=1033060](http://ubuntuforums.org/showthread.php?t=1033060)

---

### Post by JEdwardP on 2009-01-11
Thanks again Hansdown,

I think my problem is this bug, which I finally managed to search out in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/315373](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/315373)

---

### Post by blackened on 2009-01-12
Any of you tried turning off the Wallpaper plugin in CCSM then restarting X?

---

### Post by traga2whiskys on 2009-04-22
In Linux Mint (based in Ubuntu) we have been experiment the same kind of problem, but we already solved it, well someone solved it, two of us tried, and in fact it never happen anymore. Here's the solution by user of Linux Mint Forum PLURALDAVE:

> Mint main edition? I think this is the brasero 0.8.4/nautilus bug, nothing to do with compiz.

Choose one of these solutions:

1. Revert to Brasero 0.8.2[INDENT]Go to synaptic, search for brasero.
Package>Force version - Force to 0.8.2
Packages>Lock version to stop it updating again.
[/INDENT]2. Update to Brasero 0.9.1 (Felicia only if Elyssa is also affected)[INDENT]Visit [http://www.getdeb.net/app/Brasero](http://www.getdeb.net/app/Brasero)
Choose 32 or 64 bit (Felicia = Intrepid)
Download and install both .deb files: "libbrasero-media0" and "brasero" - in that order.
[/INDENT]Check if it works and then reply please in order of rme to confirm if in ubuntu its the same solution.

---

### Post by navneeth on 2009-04-29
> **traga2whiskys said:**
> In Linux Mint (based in Ubuntu) we have been experiment the same kind of problem, but we already solved it, well someone solved it, two of us tried, and in fact it never happen anymore. Here's the solution by user of Linux Mint Forum PLURALDAVE:

Check if it works and then reply please in order of rme to confirm if in ubuntu its the same solution.

For me the Desktop icons disappear, right-click doesn't work and Nautilus stops functioning whenever I insert a CD. 

Looking at the message from the log viewer, it appears that this issue may have something to do with Brasero. You can find the details [here](http://ubuntuforums.org/showthread.php?t=1141433).

I have tried removing Brasero, but that doesn't seem to be the solution.

---

### Post by Paulzy on 2009-06-13
> **the.original.kermit said:**
> I am also having this exact issue, mine happened the same way.  I'm not sure what it is, did anyone figure this out?

Using the above answer will solve the issue. Alt-F2, type gconf-editor. The follow apps > nautilus > preferences, select the tick box for "show desktop". Then Quit. The icons should appear. recall, you had to un-tick this for the multiple wallpapers to work correctly. :)

---

### Post by yogm2k on 2009-07-07
Hi...  I am facing same problem here...

---

### Post by tgrk on 2010-01-04
I fixed it simply by restarting nautilus.

---

