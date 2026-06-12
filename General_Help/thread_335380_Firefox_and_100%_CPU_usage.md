---
title: "Firefox and 100% CPU usage"
date: 2007-01-10
forum: General Help
---

### Post by bofphile on 2007-01-10
Every time I'm loading a new website on a tab with Firefox, CPU usage goes up to 100% for about 1 sec.
I've already tried to disable IPV6 with no effects and I've also tried Swiftfox and Epiphany (although with Epiphany it's a little faster)
My graphic card driver are correctly installed:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

I'm also using a laptop with a Turion64 1,6GHz and 1,25Go of RAM.
The extensions installed with Firefox are:
- Adblock Plus
- Flashblock
- gTranslate
- Image Zoom
- Menu Editor
- Tabbrowser preferences

It's really annoying and it makes the web surfing a little unpleasant (particularly when I load multiple tabs in the background, the CPU usage stays at 100% for a few seconds and I can't scroll the webpage smoothly). Moreover I don't have this issue with Windows.
I hope someone can help me. :(

Sorry for my english.

---

### Post by zgornel on 2007-01-10
There's not much you can do. Try disabling the extensions and see if it uses less CPU. I use no extensions and it still eats up cpu. Same in Windows.

---

### Post by bofphile on 2007-01-10
I've already tried to disable all the extensions and it changed nothing. Thanks for the advice though.
I'm afraid I have to live with that. :-|

---

### Post by 0xDEFACE on 2007-01-10
awww... i have the problem like this, in particular when i try download something. I guess, that GUI is guilty...

---

### Post by zgornel on 2007-01-10
It's a "feature" :D

---

### Post by andytof47 on 2007-01-13
Yeah I Got the same problem

Anyone help?

HEHE it's a "feature" Like that one

---

### Post by Zimmer on 2007-01-13
Check the system monitor to see if it IS Firefox using the CPU. I had this problem a while back and it was a Perl process linked to Nautilus that was lingering . Killed the Perl process and all was fine...No idea what it was or what other app had set it off... have not had any problems like that since ...  v strange..

---

### Post by orb9220 on 2007-01-13
My tabs (sites) always go to 70-80% on a 1.3ghz system for a few seconds. With occasional spikes to full 100 for 2-4 secs. 

1) Maxed out sites with all kinds of ad's,flash,and garbage. And poorly designed ones.
2) Java ( Yes I said Java sucks!) and suck's even more on ubuntu than Windows. It is a resource hog no doubt about it.

I can really hang firefox 2 which seems prone to more crashing, when going to like google reader which is heavily into java.

---

### Post by bofphile on 2007-01-13
I'm sure this is firefox, I've checked with the system monitor and the command top.

---

### Post by EnderTheThird on 2007-01-13
You could try installing Swiftfox (very easy via Automatix2).  It's just a more optimized version of Firefox for your CPU so you might have some luck with it.  All of your plugins and extensions and everything will still work too.

---

### Post by dehmmy on 2008-03-26
[FONT="Verdana"]> **zgornel said:**
> There's not much you can do. Try disabling the extensions and see if it uses less CPU. I use no extensions and it still eats up cpu. Same in Windows.

Same here. Firefox shoots up to 100% on runtime. Konqueor is slow as well. It was not this way when I first installed as far as I remember.

I experience NO problems in Winblows. It's lightning fast.

Quite odd and VERY VERY annoying as sometimes I have to kill it.


**_System:_**
  Dell Inspiron 6400 (E1505)

Kernel: Linux warcrime 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

**_CPU:_**
  Intel Core 2 Duo (Conroe/Allendale B2) / Core 2 Extreme Processor (Conroe B2) / Dual-Core Xeon Processor 5100 (Woodcrest B2), 65nm
  (multi-processing synth): hyper-threaded (t=2)
[/FONT]

---

### Post by spaceboy909 on 2008-04-01
I hate to complain but.........well, I've complained about Windows problems for 10 years.....

My overall experience with Linux, presently Ubuntu, is that it hogs resources so bad it makes Windows look like a starving bean pole, and I'm not kidding one ounce.  I do have resource issues in Windows sometimes, but not nearly as bad as with Linux, and this includes Firefox.

I'm getting the feeling that this is.......'just the way it is in Linux', that it's just one of the downsides we have to live with.  Am I pretty close to the mark there?

I realize people with late model systems probably won't feel it as bad.  My box is almost 5 years old now, an Athlon XP 1800 OC'd to 2000 (@1.73GHz), 512Mb Ram, but yet.........it still handles Windows XP pretty darn good for its' age.

Firefox gets so bad sometimes, especially with flash (ugh....flash has ruined everything), that it virtually stalls out my computer.  Incredibly, I've actually began to do reboots out of desperation to try and solve problems like I used to with Windows 98.

Perhaps desktop Linux is really not intended to be a serious OS for anything other than late model systems, regardless of what the marketing says.  Afterall, we now have more and more programmers using higher level, and less efficient languages simply because "the hardware is fast enough now".

---

### Post by stealth17 on 2008-05-11
> **spaceboy909 said:**
> I hate to complain but.........well, I've complained about Windows problems for 10 years.....

My overall experience with Linux, presently Ubuntu, is that it hogs resources so bad it makes Windows look like a starving bean pole, and I'm not kidding one ounce.  I do have resource issues in Windows sometimes, but not nearly as bad as with Linux, and this includes Firefox.

I'm getting the feeling that this is.......'just the way it is in Linux', that it's just one of the downsides we have to live with.  Am I pretty close to the mark there?

I realize people with late model systems probably won't feel it as bad.  My box is almost 5 years old now, an Athlon XP 1800 OC'd to 2000 (@1.73GHz), 512Mb Ram, but yet.........it still handles Windows XP pretty darn good for its' age.

Firefox gets so bad sometimes, especially with flash (ugh....flash has ruined everything), that it virtually stalls out my computer.  Incredibly, I've actually began to do reboots out of desperation to try and solve problems like I used to with Windows 98.

Perhaps desktop Linux is really not intended to be a serious OS for anything other than late model systems, regardless of what the marketing says.  Afterall, we now have more and more programmers using higher level, and less efficient languages simply because "the hardware is fast enough now".

You need to use a different window manager. Gnome does use a lot of resources on older machines in my experience. Switch to Fluxbox and you will see that thing come alive. As for Firefox, use Firefox 3 Beta 5, it's lighting fast and most of the memory leaks have been fixed. Flash is slowly improving as well, just hang in there.

---

### Post by DocHoliday52090 on 2008-05-11
> You need to use a different window manager. Gnome does use a lot of resources on older machines in my experience. Switch to Fluxbox and you will see that thing come alive.

For what? Why should he switch to a featureless minimalistic window manager just to run linux? That's not a solution. 

Listen - Firefox is having major problems right now. It's a horrible resource hog no matter which way you look at it. Try an alternative browser like Opera or Epiphany. GNOME is not your problem. 

The new Opera beta is lightning fast.

---

### Post by spaceboy909 on 2008-05-11
> **stealth17 said:**
> You need to use a different window manager. Gnome does use a lot of resources on older machines in my experience. Switch to Fluxbox and you will see that thing come alive. As for Firefox, use Firefox 3 Beta 5, it's lighting fast and most of the memory leaks have been fixed. Flash is slowly improving as well, just hang in there.

I'll check both of them out.

> **DocHoliday52090 said:**
> For what? Why should he switch to a featureless minimalistic window manager just to run linux? That's not a solution. 

Listen - Firefox is having major problems right now. It's a horrible resource hog no matter which way you look at it. Try an alternative browser like Opera or Epiphany. GNOME is not your problem. 

The new Opera beta is lightning fast.
I will check out the new one, but.....I used Opera for 7 years, from v.6 to date, although the last 2 years I barely use it anymore.  It has become the worst resource hog I could even imagine.  The only thing worse would be if it popped up a message and said, "You don't have enough ram; computer shutdown in progress"!  :(

I absolutely love Opera's features, but between the insane resource issues, extreme shutdown times and the inability to even load some of my basic sites anymore, such as Yahoo web mail (I'm referring to the windows version there), I've had to give it up, sadly.

But I don't like any other browsers out there!  It's incredible, that even with all of the choices there are, each one of them has serious issues that doesn't really make it stand out from the rest as a clear choice.  I guess I gotta start my own company!  :(

---

### Post by zgornel on 2008-05-13
Firefox 3 b5 does not seem to have any CPU usage issues ;) at least from what I observed in a two week normal daily usage.

---

### Post by cygnus-X1 on 2008-05-15
I've been learning Ubuntu 8.04 for a couple weeks and have noticed things moving progressively slower. Using the TOP command, I have been observing what is happening and when. My system has a P4 2.4Ghz CPU, 1 gig of RAM and an ATI 9600XT video card. The biggest culprits at being CPU hogs are Firefox 3 Beta 5 and Xorg. Xorg usually pulls more resources until Flash or Java kick in. Anytime anything Flash or Java starts running, the CPU tachs out at between 87-97% usage for Firefox/Xorg, with Firefox gobbling up as much as 93% alone. And it lasts more than just one second. It's more like 2-5 seconds. They idle at around 25% combined. Also, I tried using the ATI Xorg driver, but it drug things down so slow that the screen grayed out significantly more with the driver than without it. (Note: Trying EnvyNG at present.)

I've never had that kind of usage problems with Firefox 2 using the same system setup, but having Windows 2K as the OS. I've seen the term annoying being used. I think it's more like intolerable. If this is a Firefox problem, hopefully they can get the usage issue fixed, because everything else I've worked with in Ubuntu has been great to awesome, to say the least. If anyone has any ideas/fixes that may work in this situation, by all means, "spill the beans"!  :lolflag:

---

### Post by cygnus-X1 on 2008-05-15
Follow up: I don't know about anyone else, but I cannot recommend EnvyNG at this time. It took me the last few hours to get it off the machine as it almost crashed the system. First the reboot failed. When I would go to log on, it would loop back to the logon box. I went into recovery boot and let the machine try to fix the packages and X. Then I could log on. When I got logged on, a 386 machine would have been faster! Slow is an understatement! TOP showed Xorg was using a minimum of 60% and would max out anytime I did anything! Fortunately I didn't have to reload. This is just a heads up for anyone with a similar configuration. Good Luck!

Config: 2.4Ghz P4 / 1gig RAM / ATI 9600XT / Asus P4B533E MB / 20GB HDD (Main) / 2x-320GB in RAID1 array

---

### Post by spaceboy909 on 2008-05-16
Xorg is just unbelievable!  My cpu is smoking hot all the time thanks to xorg, firefox and rythembox.  Lots of stuttering audio.

---

