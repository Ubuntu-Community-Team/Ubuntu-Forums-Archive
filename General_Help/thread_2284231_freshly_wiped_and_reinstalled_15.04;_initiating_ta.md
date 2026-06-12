---
title: "freshly wiped and reinstalled 15.04; initiating tasks randomly chugging GUI+Mouse"
date: 2015-06-27
forum: General Help
---

### Post by eival on 2015-06-27
this was happning on my old build which had some failing parts and was a prebuilt with cheaper parts within it, but now my new build with top rated parts its still happening and the culprit appears to be Unity's GUI causing normal task initiating to resemble trying to play a game at Ultra 4K which results in a unresponsive screen and a mouse that chugs/barely moves, except all you did was simply click on the Unity search icon or tried to launch something....

i originally thought it was something with Firefox related since there are tons of threads similar based around that and it was usually being used during the incidents, how ever, this started happening before i even launched FF and was simply going thru the options setting everything up.

the only way i can describe it is, i click on an icon on the unity bar and then suddenly the mouse chugs, even trying to drop into a tty takes forever to respond

and now with my new system one of the biggest things i can use to tell its OS related, is that now my new case has a proper reset button and when i hit it, the OS promptly responds (already tested it once prior to this fresh install)

this issue started occurring VERY late into 14.04's life which is why i upgraded in the first place, but its very annoying, in rare cases i can chug the mouse over to the X an kill whatever is running, but only if the window's X is there and not hidden cause of the new "dynamically hiding" feature of Unity and  the entire time if something is playing back via any type of application, it will continue without issue, this appears to be SPECIFICALLY a graphical issue, but nothing i am doing is graphically intense.

im using a new i3-4170 which is more powerful than the old Core2 that i upgraded from and its IGP is much more powerful and sufficient than the chipset 43/45 i was using, and on top of that i can(and do) assign over 1 gig of my system memory to it leaving the other 6gigs+ for overhead, and I've disabled the Intel driver and it happens on both, unless Ubuntu is still reenabling it on restarts.

in a few rare instances when i had the system monitor open i could clearly see its not my CPU being 100%'d, my 8 gigs of RAM isnt taxed, these issues always happen right when i tell Ubuntu/Unity to do something with a mouse click, theres something causing it.

and none of this actually causes a crash so ubuntu shows nothing in its logs, and this isnt the same as when a specific app stops working and the forced kill box will popup, its the entire GUI shell with even falling back to a tty terminal taking forever to respond, even when it does load just typing in the login info takes forever, its faster to just hit my restart button, thankfully my new build finally gives me higher level control above just the OS so i dont have to hardreset like i was before (which is even more surprising that my HDD is still pristine just did a forced SMART test and 100% passed)

im just trying to find out what feature/option/setting in Ubuntu is causing this and how to stop it cause its COMPLETELY random, i can be heavily tab browsing, playing back video in VLC for hours and nothing, but then like right when i did a fresh install, i DARED open 2 different menus and just completely killed the UI, thankfully it resolved itself those times, most times it doesnt.

and this isnt the same as when Unity wont immediately open a program, ive had that happen before, i click on FF and it will flash but not open till later, presumably cause im doing heavy tasks and its further back in the processing que, if thats the case, thats still 100x better than if this is a bug of that feature and it just tries to load it causing issues.

---

### Post by eival on 2015-07-10
im pretty sure i finally realized what the issue is, which is burried in Ubuntu, but while trying Ubuntu-Gnome which had a tweak tool already installed and on the main dash they had a workaround called Diasbled PAT Memory which even states this exact issue and to fix it simply enable it.

i think its kinda B.S. the fact that while googling and asking about these issues for literally the last 2-3 years and never once see the word xdiagnose uttered once and they dont even have it get auto enabled if the OS doesnt see any GPU's plugged into your PCI slots

=================

EDIT - issues still ocurred even just installing and doing a basic setup, pretty sure the issue is with Compiz, and have since switched to Ubuntu-Gnome 15.04

---

### Post by Vladlenin5000 on 2015-07-10
It begs the question: What Intel driver have disabled exactly? (And why?)
The Intel Graphics driver is open source and the default in any installation. And you really need it... You'd have VESA video otherwise and, not surprisingly, the issues you described are indeed typical of a graphics driver mismatch.

---

### Post by eival on 2015-07-11
> **Vladlenin5000 said:**
> It begs the question: What Intel driver have disabled exactly? (And why?)
The Intel Graphics driver is open source and the default in any installation. And you really need it... You'd have VESA video otherwise and, not surprisingly, the issues you described are indeed typical of a graphics driver mismatch.


unfortunately just after disabling those features it still locked up, ive since installed Ubuntu-Gnome after realizing that you can replicate the unity bar perminatly with one of the extentions and none of the graphical/memory bugs/issues with the Unity UI, which means Compiz is probably the main culprit.

ill check out Ubuntu Vanilla when ever they make the major backend changes in the coming years, but will stick with Ugnome for now

---

