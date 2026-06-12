---
title: "Random Temporary Stall in Gutsy"
date: 2007-11-01
forum: General Help
---

### Post by Ultimadlamer on 2007-11-01
I'm experiencing some very random stalling issues in Gutsy (7.10), just as I did prior in 7.04...  I never had these issues in 6.06, so this is very frustrating.

The symptom:
A random total stall for approximately 10 seconds duration on average.  The mouse moves, but that's it, everything else stalls, including the performance monitor in the title bar.  I frequently use this computer for playback of multimedia files (avi, mkv, wma, etc) and if a stall occurs during playback, the sound continues to play.  Everything catches up afterwards, video stays synced afterwards (prompting a 10-15 sec rewind, bah) and I can't seem to figure out what is causing the stall.  I've had it happen with "nothing" open besides Firefox and whatever gnome/OS stuff that is loaded by Ubuntu.  It's not uncommon for this sort of stalling to occur 5 or 6 times during the duration of a single 30 minute stretch of video.  VERY VERY annoying.

What I don't know how to do:
I don't know how to track down what process is slamming my computer.  I'll describe my system specs further down, but it is a dual-core machine, and the process monitor I put in the menu bar shows that after the stall, for the duration of the stall my processor was running one core to the max.  The graph shows that the processor stays at roughly 50%.  I assume that this means that the primary core just got dominated by something.  However, since even the video freezes for the duration of the stall, I can't see any process monitor during the event, so I can't see what process just slammed me.

My system specs:
It's a fairly straightforward dual-boot Ubuntu/WInXP system.  The hardware is an HP Slimline s7600n.  The system is a dual-core 3800+ AMD with 1.5GB of RAM.  It's primary network connection is through wireless.  I'm using the Nvidia binary driver and Compiz since it's now included in gutsy.  The copy of Ubuntu is NOT an upgrade, I wiped the partition and installed from scratch when 7.10 came out.  It's hooked to an Olevia 32" TV screen.

It's really sad because the Windows XP partition can play the video just fine with no hiccups whatsoever, but I would rather run completely in Ubuntu if possible.

---

### Post by HermanAB on 2007-11-01
It is a bug in the HAL Daemon CDROM code.  Either change your CD drive for a different model, or kill this one:
$ sudo killall hald-addon-stor

You have to kill the damn thing each time you start up, so put it in rc.local or some such.

'Hope that helps!

Cheers,

Herman

---

### Post by Ultimadlamer on 2007-11-01
Thank you, I followed your advice and it indeed solved the problem.  Now that I know the culprit, some quick searches mention that it occurs AFTER installation of the graphics card driver.  I wonder if this is Nvidia's doing with the binary driver or if it's mainly a bug in the HAL daemon.

Also, the HAL Daemon apparently is responsible for doing something regarding passing media states to the computer.  Does killing the process at startup like that cause any sort of negative effects?  I don't use the CD/DVD drive much, so replacing it seems silly, but I would like to know if I could expect this fix to make any DVD burning/reading programs not respond properly in the future.

---

### Post by Ultimadlamer on 2007-11-07
I had thought this solved the problem.  Apparently I am mistaken.  This problem recurred on me today quite a bit while I had the entire hald system ended.  There were no "Hald*" processes showing in the process viewer, yet it kept freezing on me during video display.  Ugh, annoying.

---

### Post by vsanghvi on 2007-12-27
I have the exact same problem on an hp dv2000 with a new install of gutsy. I'll try this fix and see what happens, but if you find a solution that works, please let me know. I'm hoping this doesn't render my cd rom drive useless. I don't really ever use it much, but it's something that should be working. 

One thing to note, though, is that i can't recreate the problem with compiz disabled. So I wonder if it's the same issue. 

Edit: killing hte process stated in an earlier post had no effect for me.

---

### Post by Ultimadlamer on 2007-12-27
vsanghvi:  What graphics card is in your DV2000 notebook?  An Nvidia 6150 by chance?

There are a lot of DV2000 series, the actual model should be on a tag on the bottom of the notebook.

---

### Post by vsanghvi on 2007-12-28
Ultimadlamer, i have a nvidia geforce 6150 and my laptop is a dv2416us. Thanks!

---

### Post by Ultimadlamer on 2007-12-28
Reason I asked is because I noticed the same thing.  It seems that the NVidia driver is the only thing constant against these reports of freezing.  This is unfortunate, as the whole Compiz experience is what drew me to actually install Ubuntu on my lil HP here in the first place.  If I can't run compiz, I might as well run Windows.  The whole purpose of this machine here is to browse the web and to watch vid files streamed over windows networking from my main computer.  Perhaps using a different version of the Nvidia driver would help, but I've got no urge to actively troubleshoot this issue like that. 

Sadly, the random freezing when running with Compiz has sent me back to XP.

---

### Post by vsanghvi on 2007-12-28
that's too bad, but totally understandable. I really don't want to mess with drivers and stuff too much, it always seems to lead me into trouble and day long debugging sessions. i'll prolly stick with it, and just disable compiz whenever it causes me problems :-/ and hope for the best come april. if i come across something, i'll let you know

---

### Post by Kristopher on 2007-12-28
Same with me, freezing and i have HP Pavilion DV6000 with Nvidia....only started recently and am sure there was an Nvidia update recently:(

---

### Post by Ultimadlamer on 2007-12-29
Kristopher:  Your bug is somewhat different, I've seen plenty of threads detailing "freezing" with the newer nvidia driver for the 7xxx series boards.  It's due to some "regression" in the software or something.  But for us 6150 users, it's a damned-if-you-do and damned-if-you-don't situation, because the reason I upgraded my driver when 7.10 was released to the brand new one that Nvidia released was due to them fixing the black-window bug in Compiz.

So either I revert my driver to an old one without freezing but with the black window problem, or I stick with the freezing under compiz...  or use Windows because without compiz, the PC is doing nothing that I couldn't do already under windows without complications.

---

