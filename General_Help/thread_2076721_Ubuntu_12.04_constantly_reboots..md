---
title: "Ubuntu 12.04 constantly reboots."
date: 2012-10-26
forum: General Help
---

### Post by lemwt on 2012-10-26
I have recently switched from Ubuntu 10.10 to 12.04. After doing this, my computer now reboots several times a day and it has never acted this way before. I would have an average uptime of three weeks with all previous distros on the same hardware.

At this point I can safely say that this IS NOT a temperature or fan related issue.

When my system reboots, it actually restarts and stays stuck on the normal motherboard boot screen. At that point I do a hard reset and when it comes back on I'll always see a screenshot of what the monitor was displaying at the moment it reset. That flashes on for a second and then goes to the login screen.

I also get the 'mostly-horizontal, bad-TV-reception-static lines' going across my screen evey time I start the computer since using 12.04. I've seen this mentioned in these forums before and I'm just trying to provide more information. This 'static screen' always displays right before the login screen comes on (even on normal start-up)

Before I go on, here's some of my system information:
```
Ubuntu 12.04.1 LTS Precise 32-bit
Kernel Linux 3.2.0-32-generic-pae (i686)
GNOME 3.4.2
Processor: AMD Phenom(tm) II X4 965 Processor × 4
Biostar motherboard
4GB 1333MHz RAM
Hitachi Deskstar 3.5 Serial ATA Internal HDD 1TB
```

I am able to recreate this crash consistently in three different ways at the moment:

*Always restarts a little bit after starting to rip a DVD in HandBrake.

*Always restarts after uploading a specific .png image to a specific site to add captions (Firefox).

*Always restarts when moving files from one (encrypted, internal) HDD, to the main (encrypted, internal) HDD. Now I move them to an external USB drive, then back to the HDD and that works.



Those are the only three ways I can recreate the problem consistently, but it's rebooted during lots of other times such as:

*Using the default image viewer (alone).
*Using VLC (alone).
*Using flash only in Firefox alone (several times, but I cannot recreate it). 
*Just starting Firefox
*While installing updates in Update Manager (/usr/bin/update-manager).
*During other normal/basic operations I can't remember exactly.

Using Update Manager today, I installed an AppArmor update and it rebooted several times while trying to install it (everything was ok up to that point). When I would reboot myself, every time I tried "/usr/bin/update-manager" it would just crash and reboot right away. I finished the update using the update option in the task bar and have not tired opening Update Manager since.

Also, while doing that at the same time today, I began writing this post on Leafpad (text editor). Now, since it's crashed so many times, Leafpad won't even start anymore.

Attached is "syslog" for the last two hours or so. This is when the AppArmor update crashed several times, Firefox crashed as soon as I tried to open it and Leafpad stopped working. I tried to add it to this post first, but it just timed out trying to preview. Then I tried to attach the txt file but I had to cut it from 389.1 kB to 19.5 kb so most of it is missing.


One more detail I can think of to add:

Only once when it reset while using HandBrake, my motherboard screen said: "COMS checksum bad" and I had to tell the BIOS what drives to boot from again to get it to restart.


I am not the most savvy Ubuntu user out there but if anyone could help point me in the right direction to troubleshoot this it would be much appreciated. My questions are:

How can I troubleshoot all this rebooting business and try to get stable again? 

And (extra credit question), any ideas on how to get Leafpad working again?

Thanks!

---

### Post by MG&amp;TL on 2012-10-26
All of what you're saying (random reboots, images from the OS displaying on BIOS messages, CMOS corruption) is saying 'hardware issue' to me. What happens if you pop back onto another distro (live CD or whatever) for a while?

---

### Post by gifford on 2012-10-26
What type of video card?

---

### Post by lemwt on 2012-10-26
[please note that none of the buttons in the "Reply to Thread" work for me, hense, some of my text formats] 

@MG&TL #2
"What happens if you pop back onto another distro (live CD or whatever) for a while?"


I tried my old Ubuntu 10.04 and 10.10 CDs and got the same results with both: It gets to the first purple screen on the disc, but then it just restarts after a few moments. I don't even get a chance to choose between 'try it' and 'install'. They both did it twice before I took them out. These are the same discs I used to install Ubuntu before and I had no problems. And none of my hardware has changed since I've used any of these versions!

Then I tried the 12.04 CD and it worked normally (static lines and all). I just clicked around on a few things but I didn't try to make it restart. If it's really important to try to get it to restart using the disc, let me know and I can try to upload and caption that .png image again (one the known ways to make it restart). But I'm really trying not to damage my system.


Attached is a picture of the 'static lines' that show and have shown every time since first installing (even when using the CD only). This displays the first two seconds or so at the same time the login screen comes up (you can barely see some of the login box/text on the center-left through the lines).


@gifford #3
"What type of video card?"

I don't have a video card but in "Additional Drivers" there are two updates:
ATI/AMD proprietary FGLRX graphics driver
ATI/AMD proprietary FGLRX graphics driver (post-release updates)

"This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards."

I've installed this twice before (on earlier Ubuntu releases), but both times it caused a lot of graphics problems and I had to turn it off. So I haven't tried that again here.


Just some more additional info:
I don't think it's ever restarted while just sitting idle (even overnight). It only restarts while running or starting a program.

And except for Leafpad, today, none the programs have actually shown me a crash screen or message before the system restarts. It's more like someone is just pressing a reset button randomly.

---

### Post by kostkon on 2012-10-26
Could it be that your graphics card is dying and also causes your motherboard to short circuit?

---

### Post by MG&amp;TL on 2012-10-27
> **kostkon said:**
> Could it be that your graphics card is dying and also causes your motherboard to short circuit?

+1. If discs that worked previously no longer work, hardware failure is sounding likely. :(

---

### Post by lemwt on 2012-10-29
Hi and thanks for all the feedback! Hardware failure; well that is disappointing!


However, I installed the driver update: "ATI/AMD proprietary FGLRX graphics driver", and it's corrected the following:

*The static lines that appear at the login screen are gone.

*I was able to successfully upload that picture I mentioned earlier following the EXACT same steps as before and it worked this time.

*I tried my Ubuntu 10.04 CD and it also worked fine this time.



Unfortunately, I tried the Ubuntu 10.10 CD and I was able to get further in it this time; I was able to click "Try It", but that's when it reset again (before I could only get to the first purple screen). I tried it a second time and didn't even get that far (first purple screen again).

Trying to use HandBrake also still caused it to restart.

But now it DOES NOT show that freeze-frame-screen-shot of my desktop at the moment it crashed, like it always did before.



Now there is also another driver update: "ATI/AMD proprietary FGLRX graphics driver (post release updates)" but when I try to install that, I get this error:


```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```


After that fails, I have to download and install the original "ATI/AMD proprietary FGLRX graphics driver" again.

I tried installing the first one, rebooting, and then installing the post release updates. When that didn't work, I tried to install both one after the other without restarting in-between. I always got the same results (attached is jockey.log).



Concerning trying to make Leafpad work again, I tried "Mark for Reinstallation"; didn't work. I completely uninstalled it, rebooted, installed it, rebooted and it still didn't work. I typed "leafpad" in the terminal and got this:

```
:~$ leafpad
Segmentation fault (core dumped)
```

I tried "sudo leafpad" and it actually worked. I looked up "Segmentation fault" but I only have a vague understanding of what it is now (I assume this is a memory problem since it broke after a reboot while it was running, twice in a row). But I'm out of ideas to try to fix this now.



So, now my questions are:

Based on what happened after the driver update, does the somewhat-random rebooting still appear to be a hardware issue?

Since I'm still able to recreate the crash/restart, is there any other log I can check that might point to something more specific that I could troubleshoot? Or, is there anything else I can look into to possibly help help verify it is really is hardware failure?

How else could I go about trying to install the "post release updates" driver update?

I have no idea what to even try to do to fix Leafpad now. Any suggestions to fix Leafpad error: Segmentation fault (core dumped)?

And should I make a new thread for any of these questions, or is this all ok here?


Also, thanks again for the help!

---

