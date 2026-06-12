---
title: "GKSUDO freezes applications, ALWAYS??"
date: 2007-05-25
forum: General Help
---

### Post by dannyboy79 on 2007-05-25
Hi there, I am adamantly involved with the Fiesty Freeze thread located here: [http://ubuntuforums.org/showthread.php?t=412125&page=17](http://ubuntuforums.org/showthread.php?t=412125&page=17)

_**I know this looks very long and you're asking yourself, "I don't want to read all this" BUT I assure you, it's all relevant info including specs, what the problems are, what the solutions are that I have tried etc etc. So please, read on.**_

**Main Issue:**
I am hoping that by starting a new thread someone will see the title and help me because it might not be a similar issue. I am having applications freeze no matter what when I open them using gksudo from a command line as well as if I enter a new menu item and use either gksu or gksudo to open the app. The one that it happnes on first is gedit. I added a new menu item for gksudo gedit because I sometimes need to edit root owned files and instead of opening a terminal only to type in gksudo gedit, I added a menu entry for this, from which point I would then open the file I want to edit BUT gedit never makes it. I can't interact with it besides moving the window! I have attached a picture of what it looks like if I move the gedit window. By hitting where the X is suppose to be in the upper right corner of gedit, it does bring up a box that asks me to wait or to force quit it.  When I do force quit it, it's only a matter of time before my entire Gnome Session is brought to it's knees! Can't do anything but go to a tty and or ssh into it so that I can issue a shutdown and restart. Even if I kill the gedit process, kill the gnome-panel, restart X or whatever, the X server will never really materialize again. Meaning it trys to get to gdm but just sits there with a light brown screen but nothing else, no login box or anything else and eventually a little white box will appear in the upper left corner of the screen but nothing is in it. SO then I just go back to tty1 and do a shutdown -r now. The system appears to be fine up until I try any gksudo command.
**Second Issue:**
Another thing that will bring this gnome-session or X-server freeze on is If i have several windows open, FF, terminal, etc, etc and I want to get to the desktop, normally I can hit the little icon in the lower left corner, well as soon as I hit that, both the upper and lower panels freeze and I can't chose anything in relation to either of them, meaning I can't open ANY of the pull down menus. also, I notice that the graphics of the lower panel, like gets all shitty, hor and vert lines appear like there's some sort of graphics issue with only the panels. And again even if I kill the gnome-panels, restart X or whatever, the X server will never really materialize again
**How was Fiesty installed and environment???**
I did a fresh install of Fiesty using the live cd. I did all the updates and upgrades till the notification icon went away. Then I installed Automatix2 and installed pretty much everything in there. I also installed Tripwire, rkhunter, chkrootkit, Exim4 but didn't work, so I installed sendmail. I installed samba and all this stuff is working ok. I use the hosts file for name resolution and my Ubuntu box is the Local Master Browser for the network. The network consists of a roommates WinXP Home, My WinXP Pro box, my Xubuntu Fiesty, the Ubuntu fiesty box we're talking about, and 2 xbox's running Avalaunch with XBMC within that. It's all connected thru a Netgear WGT624 router.
**Graphics Drivers and Specs:**
The behavior is there when using nv, nvidia 9755, nvidia 100.xx.xx, or vesa so I starting to think it's not a nvidia problem. So then I need to consider a Hardware issue.
E4300 Core 2 Duo (stock Heat Sink Fan-but new Thermalblahblah on the way) 
ASRock 775dual-VSTA (stock bios)
1.5gb of DDR RAM (1gb of it is ULTRA which is tigerdirects brandname ram and the other 512mb is Kingmax value ram) 
XFX GeForce 6200 128mb AGP
5 hard drives, 3 WD's, 2 Maxtors. 2 are sata and 3 are ide
DVD-RAM writer by NEC/Sony goes by the name of Opterac (or something like that). 
Brand new 600WATT PSU
Texas Instruments Firewire Card with 4 ports
PVR-350
**Things checked and troubleshooting techniques:**
-I tested out the PSU with a tester, it checks out
-I used Memtest and the ram checks out, even tested each stick individually and together. 
-The cpu was installed using ArticSilver and the temp stays around 40 C when idle per the bios right after it's been running for awhile. (not sure how to check temp while in cli mode)
So then I looked at using a different kernel and or Kernel boot options.
-I have tried to add irqpoll, noapic, nolapic
-I have tried the -386 kernel versus the -generic kernel
-I have played with my AGP settings in the bios
-i have played with other settings in the bios (I am not overclocking that's for sure, I just want Ubuntu to work.)
-I have even tried the powernowd solutions that are a fix for some people, that does NOT help me!

Is there some file located anywhere that I have to remove to solve this gksudo issue? There are 2 things I am about to try when I get home from work. I am going to add a new user, then add him to the same groups that I am in and see he can gksudo. If that works, then I'll just do a reinstall and hope that solves it. I will be sure to check the issue as I install stuff. Can someone please help me troubleshoot this?

[[IMG]http://img511.imageshack.us/img511/7139/geditfrozenle2.th.png[/IMG]](http://img511.imageshack.us/my.php?image=geditfrozenle2.png)

---

### Post by dannyboy79 on 2007-05-25
polite bump, as I am sure there has to be some users that know how to troubleshoot weird issues.

---

### Post by FuturePilot on 2007-05-25
Is gksudo gedit the only function that freezes Feisty? What happens when you open Synaptic and enter your password? Any gksudo function used to cause my computer to freeze (not Feisty though) with the old Legacy driver as long as I had the RenderAccel option enabled. If I disabled it everything was fine. It might be a long shot and I know you're not using the Legacy driver, but maybe try disabling that option. Although I'm pretty sure it was a Legacy driver issue as that doesn't happen with the 9631 driver and I have that option enabled. Still worth a shot though.

Good luck. I hope someone else might have some more/better advice than I do.

---

### Post by dannyboy79 on 2007-05-25
UPDATE FROM ME.
I am happy to inform everyone that a fresh install of Fiesty (no other hardware changes) has fixed the issue of the frozen commands when using gksu or gksudo which would eventually bring gnome-session and or X-server and or gnome-panel to it's knees. Meaning I could only exit to a tty or ssh into the box to restart it. So it obviously had something to do with something I installed along the way. Apps include pretty much everything in Automatix2, rkhunter, chkrootkit, tripwire, Exim4 and then sendmail, samba as a local master browser, and ssh. I can't think of much else I installed. Obviously the nvidia from the restricted modules manager, then the 100.xx.xx which both had this freeze. Then the freeze even occured in nv and vesa so who knows what the cause of it was I am just glad it's gone and I'll be sure to check it before and after every single I install!!!

There are 2 errors I am getting now that I am not applying any boot options like noapic or nolapic, they are:

[    2.937741] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85989c), AE_BAD_HEADER
[    2.937854] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df8597fc), AE_BAD_HEADER

We'll see how it goes from here.

---

