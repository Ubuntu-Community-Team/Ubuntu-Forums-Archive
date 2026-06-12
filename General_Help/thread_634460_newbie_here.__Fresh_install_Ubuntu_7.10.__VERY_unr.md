---
title: "newbie here.  Fresh install Ubuntu 7.10.  VERY unresponsive/choppy"
date: 2007-12-07
forum: General Help
---

### Post by Steve05TSX on 2007-12-07
not sure what's going on here.  First I just installed Ubuntu yesterday, this is the first night it was left on.  I just got back to it and have been going for about 15 minutes, this thing runs like crap.  Windows when clicked on can take 5 seconds to pop up, visual effects are very slow and choppy.  Even scrolling down a page can be laggy. 

Also since I have installed the visualizations on the media player have been very laggy.  

I don't know what's going on here and I don't have an out of date computer

Machine specs are 

C2D E4300 @ 3.0ghz
Radeon X1950 Pro
2gb DDR800
320gb 7200 RPM HD

any ideas or tips would be appreciated

---

### Post by underdog512 on 2007-12-07
do you have the proper drivers installed for your ATI graphics card?

---

### Post by approaching on 2007-12-07
and this is just speculation, so please take my advice with a grain of salt. you have an x1950 pro, i have one of those too, good luck in your endevours. look into something called envy, it installs the drivers for that card, but you may want to just go into your restricted drivers manager (system>admin>restricted) and enable the driver there. but that would explain why you have a choppy system. that card doesn't come with drivers enabled by default as the main driver (fglrx) is proprietary, and therefore restricted. not to mention you saying that you have compositing (compiz) enabled, so you are running all of that off of your cpu (not so good). but other than that, you have a very simular system to me 3.2 ghz dual core, 2gb ram, 250 g hd. but that card is a lil bugger, the drivers work, but it's kinda something that once it works, be carefull when you change things. and make sure that you back up your /etc/X11/xorg.conf before you do ANYTHING.

---

### Post by Steve05TSX on 2007-12-07
> **approaching said:**
> and this is just speculation, so please take my advice with a grain of salt. you have an x1950 pro, i have one of those too, good luck in your endevours. look into something called envy, it installs the drivers for that card, but you may want to just go into your restricted drivers manager (system>admin>restricted) and enable the driver there. but that would explain why you have a choppy system. that card doesn't come with drivers enabled by default as the main driver (fglrx) is proprietary, and therefore restricted. not to mention you saying that you have compositing (compiz) enabled, so you are running all of that off of your cpu (not so good). but other than that, you have a very simular system to me 3.2 ghz dual core, 2gb ram, 250 g hd. but that card is a lil bugger, the drivers work, but it's kinda something that once it works, be carefull when you change things. and make sure that you back up your /etc/X11/xorg.conf before you do ANYTHING.

yeah I have the proper drivers for my card and used envy to install it.  My point is  that this thing should run flawless.  If this operating system actually challenges my computer with a little show effects, then there's something wrong.  I don't have anything outrageous.  It seems to be something with my computer display being off or for being inactive for so long, honestly I have no idea.  

It ran fine the day that I installed it that's the way it should always run.

---

### Post by Steve05TSX on 2007-12-07
bump

---

### Post by patty mac on 2007-12-08
A thought: I believe envy just downloaded the latest installer from the ATI site and runs it.  The ATI installer doesn't let you know if you didn't have the proper kernel headers to install the module, so you probably have the xorg driver but not the kernel module.  If that's the case, then you can't just download the kernel module as it's for a different relase.  The easiest thing to do would be to install kernel headers for your current kernel and then re-run envy.  If that doesn't work go to ATI's web site and download their script - it doesn't take any effort.  Anyway, I don't know what the package name is for the kernel headers on ubuntu, but one way to get it, and get software that you probably need anyway, is this:

$sudo apt-get install module-assistant
$sudo m-a prepare

That will get you everything your computer needs to build the drivers.  Let us know how well that worked...

---

