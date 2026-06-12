---
title: "Ubuntu on Chromebook 15"
date: 2016-01-13
forum: General Help
---

### Post by awilson555 on 2016-01-13
I have downloaded the xfce4 on a chromebook 15 to play minecraft. I was successful with it but only for a little bit. It seems to have uninstalled itself. I was able to play minecraft i then used the alt ctrl shift forward command to switch to chrome OS to watch youtube for a few days and now I am unable to use the keyboard command to go back to linux. I went to the command console to reenter commands to run linux and they all came up as an error. Is anyone familiar with this? What should I do to play minecraft on the chromebook 15? Thanks. :)

---

### Post by TheFu on 2016-01-13
Dual boot? Chrubuntu? Chrooted?  How you set this up matters.  Did you remove any write-protect screw?

Also, be careful. I have a bricked Acer C720 because I wiped ChromeOS 2 yrs ago and installed Ubuntu. Everything was fine until I had to remove battery power from the device to replace a keyboard about 6 weeks ago. From that point on, it doesn't see any OS and ChromeOS recovery steps are useless.  I never changed the default BIOS.  Plus I tested the recovery steps 2 yrs ago and they worked fine.  The ChromeOS Ninjas weren't helpful, sadly.

Be careful.

---

### Post by awilson555 on 2016-01-16
Hey, sorry for the late reply. I believe it was dual boot. and Chrooted. I don't believe I wiped anything. It had me go into manufactur's mode to do it. There are several how to steps online but it doesnt seem simple. Any idea on how to put ubuntu on the chromebook? A good walkthrough?

---

### Post by TheFu on 2016-01-16
Chromebook 15 is extremely vague.  You'll need to do the research yourself and know that bricking the device is possible.
Find where someone has EXACTLY the same model (not just "Chromebook 15") that you have.  Think there are about 30 different chromebooks easily available today. Each is a little different for putting a normal Linux on. Sorry.

Dual-boot AND chrooted? Huh?  I suppose that is possible, but, but, but why?  Never heard of "manufacture's mode."  Usually chromebooks need to be in developer mode to do anything besides run ChromeOS.  Exact, correct, details matter. If you aren't detail oriented, maybe best to leave it alone?

For example, I have a Chromebook 2 (2015 edition) and the vendor has made 4 different versions of that same "model."  When I look at the insides for mine, it doesn't look like the insides for those I find on Youtube just 3 months ago.  I've see 2 other videos, each with different insides and neither match what is inside mine. ;(

OTOH, this new machine is like a $1000 ultrabook for $400, so I'm willing to have a few hassles to get it working.

---

### Post by awilson555 on 2016-01-17
I googled the exact model number and found something. On my phone now will post the direction page I used. I went into developers mode. "Manufacturers mode" is a term I used as substitute due to short term memory. I actually got it working but didnt appear to stay after logging off mine craft and switching back to chrome os. Linux completely wiped?

---

### Post by TheFu on 2016-01-18
> **awilson555 said:**
> I googled the exact model number and found something. On my phone now will post the direction page I used. I went into developers mode. "Manufacturers mode" is a term I used as substitute due to short term memory. I actually got it working but didnt appear to stay after logging off mine craft and switching back to chrome os. Linux completely wiped?

Don't know. What exactly did you type at each stage?  Plus there are other questions asked above which have been ignored. Cannot help with the data provided so far. Cannot read your mind, plus I'm working on 2 chromebooks here, so confusion could happen without clear, accurate, details.

---

### Post by awilson555 on 2016-01-19
the model number is cb5 571 c4g4. the manual i used is dual boot by default ([http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)). it boots linux and chrome os at the same time so i can then use keyboard commands to switch between the two. Would non-dual booting it, be better? I just want something that works. Just for clarification Dual boot means that it boots linux and chrome os? I did not remove any screw. I can follow a manual but doing it on my own without any kind of reference guide would be near impossible for me.

---

### Post by TheFu on 2016-01-20
crouton is NOT dual boot.  It is a chroot solution.

Dual Boot - [http://www.howtogeek.com/187789/dual-booting-explained-how-you-can-have-multiple-operating-systems-on-your-computer/](http://www.howtogeek.com/187789/dual-booting-explained-how-you-can-have-multiple-operating-systems-on-your-computer/) ; wikipedia also has details for this and many other common technical terms.

Chromebooks are NOT normal PCs and if there is any part of chromeOS on the machine, google may try to patch and put it back to the factory std OS.  When in Developer mode, at boot on my devices, there is a warning that the OS verification has been disabled, so google offers to fix it with a space bar. If anyone ever does that, Linux is removed.  Google seems to work hard to ignore any other uses for these devices. Same for all the vendors I've contacted. If you don't run, stock, stable, ChromeOS, forget support. The Google support pages are less than helpful too - actually, if you even say "linux" they close the thread and claim it is a duplicate of their weak-ass "unsupported options" page ... this happened to me twice this month already.  I was just trying to use a Linux machine to create the chromeOS recovery flash drive. Never mentioned running linux on the machine - not once.  They selected a "best answer" that had ZERO to do with my issue, then closed and locked the thread.  Creating the ChromeOS Recovery flash drive on Linux **is** supported, so they shouldn't have closed any threads.

You never said the vender - not that it matters. Google is your friend and there may not be an accurate walk-thru for that model today.  

You have an "Acer Chromebook 15, CB5-571-C4G4"  - that is the walk-thru you should look for. Glad you didn't get the older version with a crap CPU. That 3205U should be happy-making for you.  My Acer C720 had a 2955U CPU that completely rocked and my new Toshiba has an i3-5015U which is about 2x faster! Whoooohoooo!  I've spent the last 2 days trying to get it to boot a plain Linux. Installations seem fine, but the first reboot never comes back. I've waited an hour - with the "Booting from 1st hard disk ...." message - no joy.  Haven't bricked it. Keep having to go back and restore ChromeOS and start all over with reflashing the ROM and toggling some firmware settings.  I wrote some notes on a 3x5" card about all the steps so I don't forget.  Tried Crouton on Sunday - meh.  I don't like the file-by-file encryption that crouton does and that the ChromeOS kernel is still running underneath. I am loving the 1080p on this 13inch monster, however.  Didn't have anywhere near this amount of trouble with the C720.

I won't insult your intelligence by providing links that google could provide easily. [https://www.reddit.com/r/chrubuntu/comments/391mh5/help_thinking_about_getting_the_acer_chromebook/](https://www.reddit.com/r/chrubuntu/comments/391mh5/help_thinking_about_getting_the_acer_chromebook/) has lots of links. John Lewis's ROM is probably what you want, but you **will** need to open the device and remove the write protect screw to legacy boot (I'm 98% certain). That screw will end the warranty; if that bothers you, take it back and get a normal PC which are much easier to run Linux.  That reddit has overview instructions similar to what my C720 had (I vaguely recall).  If you follow it, definitely never disconnect the battery or let it run out without being in factory ChromeOS state first.  I didn't and have a brick now after 2 yrs of relative happiness. 

If all this sounds non-standard, well, that's because it is. Running a stock Linux on a Chromebook dual-booted (or even single-booted) has some dangers.  Running a Linux inside a chroot _under_ chromeOS is not nearly as dangerous to bricking, but you'll want to have excellent total system backups, so when ChromeOS updates wipe your chroot areas, you can get those back.

That's all I know. Good luck to you, whatever you decide.

---

