---
title: "100% CPU and Constant Fan"
date: 2007-04-11
forum: General Help
---

### Post by wyth on 2007-04-11
I'm trying to track down why my laptop so often jumps straight to 100% CPU and kicks on the fan.  I'm running Feisty with an ATI Radeon R250 gfx card (open ati driver), 768 mb ram, and this happened on Edgy as well.

I've read that Beagle can be a culprit, especially when your rig goes into screensaver mode.  I turned that off, but am still experiencing abnormally high CPU usage in screensaver -- I use a blank screensaver, and it roars when the screensaver turns on, which seems counter-intuitive.  When I do a "top" command from the terminal, I often see xorg or firefox as the main suspects (I wish System Monitor would tell you what program was using the 100% use from the graph on a mouseover).  I've set my CPU scaling to ondemand, but this doesn't really solve things.

As I understand it, the fglrx driver has a nice feature called powerstate; I don't know if there's a similar feature for the open ati driver (and the fglrx driver isn't working with Xorg 7.2).  I just want to keep my laptop from running constant sprints.  I almost never boot into windows now, and don't want to if I can help it, but this is really battering my system.

Any/all hints and suggestions will be considered, and more info available upon request.

---

### Post by wyth on 2007-04-13
bump

---

### Post by m.musashi on 2007-04-13
I had a similar problem with beagle. I didn't just turn it off - I uninstalled it. However, if top is showing firefox and xorg as the culprits then it might be something else.

I don't use a screensaver. I have it set to none and just have my display turn off after 10 minutes. Of course, you would think a blank screensaver wouldn't use much juice.

Let top run for a while when it does the 100% thing. I've noticed it can take a while for the offending app to show up. Post the output of top when it happens.

EDIT: one more thought. If it's related to the radeon driver you might try not using it. I use nvidia so I don't know the details but if you can just use the default driver for a while see if the problem still occurs.

---

### Post by wyth on 2007-04-13
I ran top for a while, and it's definitely Firefox.  Actually, the CPU doesn't always ramp up to 100% with just Firefox, but it'll run hot and the fans kick in.   I'm playing  around with Epiphany now, with no issues.  (But I miss some of my addons.)

I took your advice on the screensaver and haven't noticed any problems yet.  And I'd like to take your advice with the radeon driver, but fglrx isn't functioning with xorg 7.2 at this point.  It may be just something I need to wait out.  

I'm slowly inching my way to using Linux about 90% of the time, and want to knock out every reason to go back to windows that I can.  This high cpu usage and constant fans are just two more in that list.

---

### Post by m.musashi on 2007-04-13
Yeah, it always seems like there is something that is never just how you want. I have the same kinds of problems in windows - always something. At the end of the day the Linux something are usually less of an issue than the ones in windows. Maybe I need a Mac:).

Is the fglrx driver the default driver for feisty? It seems odd that the default wouldn't be working. Wouldn't that kind of be a show stopper for the upcoming release? Isn't there one called just "ati" or "radeon" or something? I mean one that isn't 3d accelerated?

I've had problems with firefox using a lot of CPU too but usually less than 50% (which is still a lot). You might give opera a try. It's pretty nice too but I still like firefox best.

---

### Post by Slipmyknot101 on 2007-04-13
Re: Wyth

~Hey, about the windows thing, not to change the thread topic or anything, but I think I can relate to the windows situation. If you want to wave bye bye to windows completely, you may want to at least keep your install disk because I recently found the whole "virtual machine" thing where I can run windows inside linux with no dual boot, no corrupt .dll's with NSA keys, none of the rumored windows spy stuff, none of the useless 90 million security updates.

Yeah so if you want to know more if you don't already know about the windows inside of linux thing, give me a PM or something so that I don't have to tangent this thread too much.

Have a good day.

Trevor

---

### Post by wyth on 2007-04-13
Y'know, I'm considering a virtual machine setup more and more often.  Two things from windows that I still need for work are Word and Dreamweaver, but until the video card is working properly, I'll keep dual-booting.

The fglrx driver is the proprietary driver from ATI.  The open ati/radeon driver works okay, and I'm on it now, but it's not great.  For instance, I just set my display to turn off, and when it came back on, I'm getting some significant screen degradation; it looks like all the edges of any straight line is growing hair.  This happens with any graphics-intensive work too, including just heavy browsing.  This wasn't an issue with the fglrx driver, and I'm willing to forego compositing for a reasonable display.

---

### Post by m.musashi on 2007-04-13
I just read in another post that there was an update to the fglrx driver in the latest feisty updates. I didn't personally verify that but maybe it will address your problems.

---

### Post by wyth on 2007-04-14
Do you have the link to that post?  I'd like to read it and see what was fixed, and if there were any more issues.

---

### Post by m.musashi on 2007-04-14
No, sorry. It was someone asking if the update listed for fglrx would cause a problem if they were on nvidia. I only noted that they pointed out an update listed. I would think somewhere they keep a change log but I've never tried to find one.

---

### Post by wyth on 2007-04-15
I think I"m going to have to wait or just give up on this.  It's disappointing, because I've never had a problem with the fglrx drivers in the past.  But I install it in the typical way [shown here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), and I've tried > Option "Composite" "Disable" and > Option "Composite" "off" and > Option "Composite" "0" in my xorg.conf, and every time I restart X, I get a "no screens" error.  

I'm wary of using the patch solution.  I tried it a week ago, a few times, to no avail, and I've not seen any info as to if it'll just automatically update with the standard xorg-driver-fglrx, or if you'll have to monkey with it every time you get a kernel update.  

I know some people have gotten the standard fglrx working.  Wish I knew what their secret was; maybe it just doesn't work with my card and Xorg 7.2.  Meh.

---

### Post by m.musashi on 2007-04-15
What card do you have (EDIT: never mind, just read your sig. D'oh)? What is the output from 
```
fglrxinfo
```
If there are issues with the xorg 7.2 and fglrx you might consider reverting to the "ati" driver until they are resolved. On a laptop I think I would rather have a cooler computer and longer battery life than effects (but that's just me).

I think you just replace "fglrx" with "ati" in the xorg.conf file to do that or run
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "ati"

I have a somewhat older laptop with an ATI chip and have never had much luck getting any driver other than ati to work well. At least I've never been able to get beryl to work on it. Don't really need it to either so I've more or less given up. I may try again when feisty is "official".

EDIT: according to [this page](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon?) your card should be supported. It's also a guide for setting up beryl and uses the "radeon" driver instead of "fglrx" so it might help.

---

### Post by wyth on 2007-04-15
EDIT: I'm already using the regular open source ati driver, but it doesn't work well with my card.  That's why I always used the fglrx card in the past.  (I'm on the ati driver now, and my screen is starting to get a little wonky.)  

I do have xorg-driver-fglrx installed, and fglrixinfo gets me:
> 
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

And thanks for the link.  However,  I've tried that before (love howtoforge), but if fglrx won't run, the rest doesn't follow. 

Maybe it's time to submit a bug?

And maybe it's time to change the open source ati driver name in xorg to radeon, and the proprietary ati driver's name from fglrx to ati.  This naming scheme just gets confusing, "ati" is open source but fglrx is the proprietary ati...

---

### Post by m.musashi on 2007-04-15
If you are going to use the open source driver you have to remove the fglrx one. They conflict somehow. Maybe that is what's causing some of the problems.

I also seem to recall reading somewhere that if "Mesa" showed up in fglrxinfo then you are actually not using the driver. There was a fix for this somewhere. I'll have to try and find it and see if actually applies to your situation.

Yes, this could be a bug but I'd suggest a thorough cleansing and setup of the radeon driver. I'd be willing to bet you could get a stable desktop but I'm not sure about eye candy and such. I have the radeon driver on my ati laptop and it works fine but no beryl. Still, it works fine and that is the most important aspect.

---

### Post by m.musashi on 2007-04-15
Okay, found the stuff about Mesa. [This thread](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+fglrxinfo) is what I used in the past but I don't know how relevant it is to feisty. However, the "Mesa proplem" might be what you need to fix to get this working.

IMHO, however, I'd focus on getting the open source driver working for now.

---

### Post by wyth on 2007-04-15
I actually am using the open source driver.  My problem is the open source driver has never worked well with my card; it's slow, and I get regular screen degradation.  I can use it, but in about an hour, I need to reboot.  

The Mesa will always show up if you're using the open source drivers, as I am right now.  However, I have fglrx installed -- I'm just not using it; that's why I can do fglrxinfo.  And fglrxinfo is giving me Mesa because I'm using the open source drivers (it should say Mesa unless I configure xorg.conf to use the fglrx drivers; if it still reads Mesa, then there's a problem).

I'll most likely open a bug on this.  After the latest kernel update I lost sound, so I'm back on windows right now.  I'm hoping this all gets sorted by the 19th release date.  (I'm a little embarrassed to say, I'm enjoying the snappiness of windows again; this is what I'd get with fglrx.)

---

### Post by m.musashi on 2007-04-15
As I understand it, if you are using the os driver you should uninstall the fglrx one.
> fglrx is the name of the official, proprietary, Radeon driver from ATI. It conflicts with the open source "radeon" driver. If the "fglrx" kernel module is loaded at boot, X will be able to start using the "radeon" driver but "Direct Rendering" (DRI) will be disabled. This results in a severe performance reduction. If you previously used the proprietary "fglrx" driver it is highly recommended to unload the "fglrx" module if you wish to use the open source "radeon" driver.
From [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Perhaps that is why you experience the degradation problem. I will need to check into this on my own laptop. I'm pretty sure I didn't uninstall the fglrx driver and I know at some point I tried to use it.

---

### Post by wyth on 2007-04-15
I appreciate the help you've offered.  With the radeon (open source ati) driver, everything checked out.  I had SGI as the vendor, and had direct rendering -- both with and without fglrx installed.  I'm not sure why things get sluggish sometimes or why the screen starts to grow virtual hair around all the edges (it gets especially bad if I'm using compiz for a while), but maybe it's a direct rendering issue; I need to look more into that.  

However, I've had the same problems whether fglrx was installed or not.  That's why I'd rather just get a working fglrx again (and I'm not the only one having that issue).  I know fglrx isn't *open*, but I also need to get work done and can't spend so much time tweaking and tuning.  If I had any skills at all, I'd be contributing to the project rather than just crying when something didn't work.

---

### Post by m.musashi on 2007-04-15
Sorry I couldn't be more help. It seems you have a good grasp of this stuff - probably better than me. I hope you manage to get things worked out. It does seem odd to have the problems you describe with the os driver and a supported card. I wonder if there isn't something else going on. Or maybe it's just one of those things with beta software. Hopefully they'll get it worked out quickly give the looming release date:).

---

### Post by RJARRRPCGP on 2007-04-15
> **wyth said:**
> I'm getting some significant screen degradation; it looks like all the edges of any straight line is growing hair.   

Is it fine under Windows after installing the Catalyst drivers? If it isn't, you probably have a bad video card or overheating video card.

---

### Post by wyth on 2007-04-15
Heh.  I wouldn't be one bit surprised if my card is going on me.  It does run a bit hot; one of my other issues under Linux is my fans run about twice as much as under windows.  But I don't have the hairy problem in windows.  Wait -- I take that back -- I *do* get a little bit of that in Google Earth when I'm zooming around.  But that's it, no other issues under windows.  It is a bit of an older card, but not that old.

---

### Post by angryhomer17 on 2007-04-16
> **wyth said:**
> I ran top for a while, and it's definitely Firefox.  Actually, the CPU doesn't always ramp up to 100% with just Firefox, but it'll run hot and the fans kick in.   I'm playing  around with Epiphany now, with no issues.  (But I miss some of my addons.).

Try swiftfox. It's optimized for Linux. [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by wyth on 2007-04-16
Thanks angryhomer, I'll give that a try.  I've always been a little stand-offish of things that aren't in the repositories, but if it calms my browsing down, it's worth it.

Also, here's a bit of an update.  After enabling the following modules in the Device section of xorg.conf, things have picked up a bit:

> Section "Device"
    Identifier    "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Driver        "ati"
    Option        "UseFBDev"        "true"
    Option        "XAANoOffscreenPixmaps"    
    Option        "backingstore"        "true"
    Option        "EnablePageFlip"    "true"
    Option        "RenderAccel"        "true"
    Option        "AGPMode"        "4"
    Option        "AGPSize"        "64"
    Option        "DynamicClocks"        "on"
    Option        "mtrr"            "on"
    Option        "ColorTiling"        "true"
    BusID        "PCI:1:0:0"
EndSection

Still a little screen degradation, but not nearly as much (and using compiz as well).  I'll finish my grading and give swiftfox a go.

---

### Post by wyth on 2007-04-16
Here's a bit of an update: With the above options enabled, I've not had any screen degradation at all.  I've been working all night without an issue.  Which option was it?  I have no idea; I've used RenderAccel, XAANoOffscreenPixmaps, AGPMode, ColorTiling and EnablePageFlip before to no avail.  That leaves backingstore, AGPSize, DynamicClocks, and mtrr; one of those, or a combination of, is doing the trick.

It does still thrash the fan some, although not as much.  I've also gone with Swiftfox, which seems to be helping a bit.  Things are looking pretty good -- thanks for the help, all of you!

EDIT: Could the thrashing fans have something to do with the recent revelation that [Gates tried to cripple acpi on anything but Windows machines]("http://www.osnews.com/story.php/17689/Bill-Gates-on-Making-ACPI-Not-Work-with-Linux")?

---

