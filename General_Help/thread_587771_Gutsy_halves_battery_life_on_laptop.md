---
title: "Gutsy halves battery life on laptop"
date: 2007-10-23
forum: General Help
---

### Post by k31k0 on 2007-10-23
Hi. I just installed Ubuntu 7.10 and everything works great except that battery life is too short. Before I had Ubuntu Feisty installed and got around 2 hours of battery life and now I get less than an hour. I did a clean install.
Can someone help me? I use my laptop for work and 50 minutes of battery life is simply too little for some serious work.

Thanks.

---

### Post by Jorn.jambers on 2007-10-23
have you already tried to see if your cpu speeds changes when you are doing noting? You can add the CPU frequency monitor to your  Panel. I think this is the reason your laptop battery doesn't live as long as it should, because your laptop doesn't scale down your cpu.

---

### Post by k31k0 on 2007-10-23
I checked that and laptop scales down the provessor's speed (when it is idle, the speed is 1 GHz; maximum is 1.67 GHz). PowerTOP says that the processor's speed is at 1GHz in more than 90% of time.

---

### Post by katakaio on 2007-10-29
Having the same issue here. With Feisty, I was averaging about 4 hours, and since performing the Gutsy update, I'm at about half that now. I make full use of processor scaling (the processor is idle most of the time anyway), and I don't see any memory hogs running. I get the same weak battery life whether Compiz effects are on or off. I heard that Gutsy was supposed to *improve* battery life, not chop it in half . . . is there something we're missing? Thanks!

(Edit: I should clarify that I don't have an HP nx7400 laptop, but I'm experiencing almost exactly the same thing. FWIW, I'm using a Latitude D420.)

---

### Post by chotao on 2007-11-27
Hey, I got the same problem as well. Battery life is short by half.
(I'm very new to Linux&Ubuntu).
Before I switched to Ubuntu, I use Vista. My battery life was about 6 - 7 hours.
But with Gusty I got just about 3 1/2 hours.
Are there any way to solve this problem?

---

### Post by katakaio on 2007-11-27
It seems strange that our battery life is getting chopped almost exactly in half. I wonder if it's some ill effect of the dynticks modification . . . what procs are you guys using? I have an Intel Core Solo (32-bit, 1.07GHz). Maybe the kernel mod works better on some processors than others.

As soon as I back up my data, I'm planning on doing a clean Xubuntu install of Gutsy. I'll report back with any findings.

---

### Post by ElTimo on 2007-11-27
How much time does gnome-power-manager estimate for each of you? For me it gives a much larger estimate than it did with Feisty, but the actual usable time is much less. I have a Dell Latitude D820 C2D 2.0 GHz 4 MB cache 2 GB memory nVidia Quadro 110m 256 MB if anybody was wondering :-P

---

### Post by dheff on 2007-11-28
I am getting this as well with Gutsy, I am averaging about 45 minutes of battery life on a Toshiba Satelitte 1,6GHz 1gig RAM Intel Centrino processor

---

### Post by chotao on 2007-11-30
Just in case you wonder. My computer is DELL Inspiron 6400, CPU is Intel 1.83 GHz, Core 2 Duo, RAM 1 GB, Integrated Graphic card.
 
I add extra battery pack when I bought from DELL. 
So with Vista/XP, it can run up to 6-7 hours unplug.
But just like I said, it can run on Gusty for 3.5 hours (that mean cut of by half).
Anyway, how about Fiesty?
Are there any battery issues with Fiesty?
If not, I'll consider to install Fiesty on my computer (I love Gusty UI but I'd love more to
see my computer battery have long life time battery).

---

### Post by ElTimo on 2007-12-04
I had an idea...from what i can tell, everyone has dual-core processors, no? and our battery life is getting cut almost <i>exactly</i> in half...I know this sounds stupid but could these two things be related? I don't know <i>why</i> they would be related, but it's just a very strange coincidence......

---

### Post by katakaio on 2007-12-06
Good guess ElTimo - and I hate to wreck your theory :oops: . I have a single-core processor, and I know of a few people with dual-cores who aren't having any issues.

In response to your first question, I think my power estimate is accurate. Maybe it's worth finding out who upgraded to Gutsy and who performed clean installs. It seems the majority of us upgraded - is that right? If so, then I really want to try a clean install and see what happens. Although if half of you guys still have this problem after doing a clean install, I'd rather not go the the trouble if we know it won't help . . .

---

### Post by rrwo on 2007-12-07
> **ElTimo said:**
> I had an idea...from what i can tell, everyone has dual-core processors, no? 

No. I have a single core processor and the life is halved after upgrading to Gutsy.

---

### Post by PriceChild on 2007-12-11
bump

---

### Post by katakaio on 2007-12-12
I asked PriceChild the friendly admin to rename this thread - it seems that our problem is a common one across multiple laptop models. Hopefully this will get us some more exposure.

I've finally formatted my Windows partition (yes!) into a /home partition, so now I can perform clean installs without losing my wares. Once final exams are done, I may give a clean install of Ubuntu or Xubuntu a spin - unless someone has already done a clean install with no luck.

---

### Post by Ertai87 on 2007-12-17
I'm going to be doing a clean install in the next couple of days.  If I notice anything, I'll get back to you.

On this note, though, does anyone know if Ubuntu includes (or has on Synaptic) a power management system for Ubuntu?  Something along the lines of Dell Quickset?  How about standby/hibernate support for when I close my laptop lid?  Thanks.

---

### Post by ElTimo on 2007-12-18
I did a clean install to begin with (two, actually- one 64-bit and the other 32) and I noticed the same problem on both...actually, it was why I did the second install! So that doesn't seem to be the problem.

---

### Post by Joeb454 on 2007-12-18
If you want suspend support...you'll be lucky :p

Although Hibernate does work on my laptop, which is nice :) Wish I could get suspend to work though :(

---

### Post by rzrgenesys187 on 2007-12-18
I have a dual-core and haven't noticed any lesser battery life, can't remember about Ubuntu but Kubuntu at least doesn't have any lesser.  Still tons more battery life than Vista but then again that's not saying too much.

---

### Post by Ertai87 on 2007-12-19
I used my laptop without battery last night and didn't notice too much reduced life.  I couldn't tell for sure cause my battery was in and out of the wall every half hour or so, but I didn't notice a significant drop in battery life over Windows XP, although I was doing less battery-intensive things like installing programs and surfing the web instead of watching video and playing high-action games.

Also, suspend support seems to work for me.  You might have to go into the battery properties in the Preferences or Administration menu and set it up.  Try that and see if it works.

---

### Post by kansei on 2007-12-19
I can confirm this. I have a ThinkPad T42 with a 2.0GHz dothan (centrino) Pentium-M.

Gnome power manager reports 4 hours 15 mins of battery life when fully charged, as does powertop (they both just pull from ACPI) and are dead on accurate. When I have 4 hours of class in a row without a place to charge my laptop, right at the end of the second class it sometimes hibernates automatically.

Pop in my windows hard drive and It reports 7 hours, 30 mins of battery life. It isn't cut exactly in half but it's close.

Have you guys all installed powertop? It's a new-ish util from Intel that helps diagnose what is waking up the processor and what kernel options and such should be set. My 4 hours 15 minutes is after running powertop and pushing the right keys when it says to in order to temporarily enable all the options. I haven't actually permanently committed the changes to the kernel and modules yet.

I will have to put yet another hard drive in and see if Hardy has this same issue. As much as I love doing all my computing on alpha releases i've told myself I won't do that on the laptop I use for school work anymore (not that I had a problem using Gutsy since early last May).

Edit: I have also noticed this on my Dell Latitude D620 running Gutsy x64 by the way. It only gets 2 hours in Gutsy vs 4 in windows. It has a 2.0GHz Core2Duo (T7200 or T7300 I don't remember, whichever one isn't the santa rosa stuff with the new socket type used on the D630)

---

### Post by asmiller-ke6seh on 2007-12-19
> **Ertai87 said:**
> I used my laptop without battery last night and didn't notice too much reduced life.  I couldn't tell for sure cause my battery was in and out of the wall every half hour or so, but I didn't notice a significant drop in battery life over Windows XP, although I was doing less battery-intensive things like installing programs and surfing the web instead of watching video and playing high-action games.

Also, suspend support seems to work for me.  You might have to go into the battery properties in the Preferences or Administration menu and set it up.  Try that and see if it works.

This is not the issue: people are expressing surprise that the estimated battery life seems to be much less in GUTSY that what they experienced before installing GUTSY - especially when GUTSY was supposed to be easier on battery usage.

If you are unplugging and plugging your laptop, you will probably not experience what others are talking about; however, you are not giving your system the opportunity to learn what the battery life is like on your laptop. This is likely to result in your not getting accurate estimates of your remaining battery life. If you are interested in getting accurate battery life estimates from the power manager in GUTSY, then you should probably unplug your laptop and use it until the estimated power gets down to within 5%-10% of estimated battery left --- and THEN FULLY recharge the battery. Do this full cycle discharge/recharge cycling 5 times or more, and you will get a more accurate battery life estimate in the future.

---

### Post by ElTimo on 2007-12-19
@asmiller
On the contrary, I have let my laptop do so, and I still have this problem. It was one of the first things i did, before trying the clean install.

---

### Post by kansei on 2007-12-20
> **asmiller-ke6seh said:**
> This is not the issue: people are expressing surprise that the estimated battery life seems to be much less in GUTSY that what they experienced before installing GUTSY - especially when GUTSY was supposed to be easier on battery usage.

If you are unplugging and plugging your laptop, you will probably not experience what others are talking about; however, you are not giving your system the opportunity to learn what the battery life is like on your laptop. **This is likely to result in your not getting accurate estimates of your remaining battery life. If you are interested in getting accurate battery life estimates from the power manager in GUTSY, then you should probably unplug your laptop and use it until the estimated power gets down to within 5%-10% of estimated battery left --- and THEN FULLY recharge the battery. Do this full cycle discharge/recharge cycling 5 times or more, and you will get a more accurate battery life estimate in the future.**
That isn't true. It pulls the full charge vs current battery capacity (ACPI) and then estimates the current wattage the laptop is using (also ACPI), then does the math to determine how long it'll last from there.

> **ElTimo said:**
> @asmiller
On the contrary, I have let my laptop do so, and I still have this problem. It was one of the first things i did, before trying the clean install.

Yeah the problem here isn't that Gutsy is lying and estimating the remaining life incorrectly (how would it manage that given how it is calculated?), it's that the actual battery life is nearly half what it is in windows.

I will be probing around with graphics card stuff to figure out if that's my problem. Maybe my ATI Radeon and also NVIDIA Quadro 120m have awful power management capabilities in linux.

---

### Post by ElTimo on 2007-12-20
@kansei:
You have a Quadro 1xxm series as well? That's interesting. Is your Ati card also a workstation card? Actually, does anyone here have integrated graphics? (Blatantly incorrect hypothesis warning) Maybe that has something to do with it?

jeez, I really have to stop thinking out loud :-P

---

### Post by kansei on 2007-12-21
yup, the dell has that nvidia quadro card. It's equivalent to a GeForce I think 7400go?

My thinkpad (also has this issue, and is the laptop I use most frequently) has an ATI Radeon 9600 Pro.. it isn't a workstation card, but the workstation equivalent is the FireGL T2. Yeah it's one of those ones where it's just a firmware change to the workstation card.

I have about 20 dell laptops I can test with sitting in my closet but they all have ATI/nvidia cards, as they are Latitudes in the C640 and D600/610/620 range.

I don't think I have anything with integrated graphics to test with.

---

### Post by ElTimo on 2007-12-21
Could it be that it has something to do with the fact that some of us are using dedicated video cards, while others are using integrated graphics? This seems like a valid idea to me (at least, more so than my previous guess about the dual cores), as neither Ati nor nVidia really seems to care all that much about Open Source users, thus their Linux drivers are considerably worse than their Doze drivers. Integrated graphics, though, should be supported as part of the motherboard drivers, correct? And there haven't been too many problems with motherboards lately that I know of.

@kansei
Can I have one? lol

---

### Post by exjinn on 2007-12-22
awesome post.

I've been having the same issues with a dual core toshiba satellite however I do regularly plug/unplug my notebook.

---

### Post by ahm911 on 2007-12-23
ahh perfect i have the same problems going on too! 
i just fixed the over heating problem ( laptopt was hittin 70c compared to 45c in xp ) but now my battery barely lasts. i used to get 3.8 to 4 hours in xp and also 4 hours + wen i tried vista but now on a 100% charge i am estimated 2:10 and whihc normally is around 20-40 mins less that is with most power options running most conservative ( 90% less brighter lcd and most other options in the power management turned down ). laptop specs are in my signature any help would be appreciated!

---

### Post by AlesUbu123 on 2007-12-25
Almost the same problem here, although the reduction I am seeing is about 30% (I am getting 5 hours battery life in XP and Gutsy demonstrates about 3,5 hours of battery life).

This is terrible and is making me use XP instead of ubuntu when running computer on battery power. 

Are we all sure that XP is not lying about the battery life or something?
Or is Gutsy giving calculations that are too low?

My computer is: 
**HP 6720s laptop**
Processor Intel Core 2 Duo T5470 (1.60GHz) 800MHz FSB
Intel GM965 Chipset
Memory 1024 MB DDRII (667MHz) (upgraded to 2 GB)
120.0GB SATA HDD
Intel Media Graphics Accelerator X3100 (up to 384MB shared memory) graphics
Screen 15.4'' TFT WXGA 1280 x 800 WXGA Bright View

---

### Post by Maximus.Psychosis on 2007-12-25
Well, I really don't know why I didn't started this... I thought it was just my battery failing, but this has clarified my 1st assumption: gusty = battery killer...

powertop is good for CPU based processing (wakeup per second) but it cannot help out with things like GPU or North/South bridge usage. Now i may not know what is going on, but I've been playing around with power processes (APCI and all that).

So far what I have discovered is that with the graphics drivers it has a power saving feature for the GPU, but I'm guessing that if you lack out on hardware rendering it also drops that feature.

in xorg.conf
>        Option          "DynamicClocks" "on" 

were I come up with this idea is that with my system (x23: 866MHz CPU, 256MB RAM, 20GB HDD, ATI Mobility Radeon 7000 with 8MB running a display with 1024x768 resolution) can not render with little as 8MB on 24bit color with a screen of 1024x768, i have to drop it to 16bit color to start the rendering (and allow the 3d desktop thingy resource chewer eye-candy)

But this is not the problem for everyone, people do have systems that can render in hardware with not a problem...

As one would guess I've been having the same problem, I had a battery that could just do 3 hours and 45 minutes on low load (low screen contrast, CPU set to low, hdd off when idle for 5 minutes) in 7.04 now its 50 min in 7.10 doing the same (bad for times when I need to work without a power point).

and I think it may have affected the charge rate too, it take 5+ hours to charge the battery for 50 minutes of work this use to be on par with charge / discharge.

my worst fear is that I will have to get a new battery for this old lappy now...

---

### Post by katakaio on 2007-12-25
First off, I gotta thank everyone who is weighing in on this issue. I'd rather be working on this with you guys than working on it alone.

> 
Yeah the problem here isn't that Gutsy is lying and estimating the remaining life incorrectly (how would it manage that given how it is calculated?), it's that the actual battery life is nearly half what it is in windows.

I will be probing around with graphics card stuff to figure out if that's my problem. Maybe my ATI Radeon and also NVIDIA Quadro 120m have awful power management capabilities in linux.

I couldn't agree more with the first paragraph. On the other hand, I'm skeptical that the graphics card is the culprit for two reasons. The first one (the big one) is that my laptop was running beautifully for four hours with this hardware arrangement, and the only thing to change was going from Feisty to Gutsy. (This seems to be a common scenario for a lot of posters.) Secondly, to echo ElTimo, I'm running an integrated graphics card (Intel 945GMS) which should be using the minimum amount of juice.

Despite those two reasons, I think you may be on the right track. If it's not the graphics cards and drivers themselves, maybe it's something to do with Compiz, rendering, &c (something along the lines of Maximus.Psychosis). I also think that ElTimo has the right idea to see if there's something shared in common amongst those with this problem.

Never give up - never surrender!

---

### Post by ogwilson on 2007-12-25
Hi guys. Same exact problem as you all, only my story is a bit different and varied.
 
Well here are my specs first of all.
 
Dell Latitude D520
Intel Core 2 Duo 1.66ghz
512 megs of ram
256 megs of shared integrated graphics (Intel 945M Accel. Graphics)
etc etc
 
I was getting 6-7 hours in XP with minimal power usage (lowest backlight, no wi-fi, and screensaving), and with wi-fi + medium backlight, i as getting 4-5 hours.
 
Now, in Ubuntu 7.10, I used to get 3 hours and 15 minutes with lowest possible power usage, and about 2:30 with wifi and medium backlight.
 
I wondered why this was. So i posted a thread on this site (it's the most recently created one in my profile) and someone directed me to lesswatts.org.
 
Well, after trying those things on that site, I can safely say that something is really screwy with SOMETHING about this distro and laptops. My battery indicator went from 3:15/2:30, to 2:15/1:50 (left side of / is without wifi and backlight, right side is with wifi and medium backlight)
 
I'm really disappointed in this and I'm ready to revert back to XP for the time being, or back to an earlier version of the distro if it will help improve my battery.
 
Also, note that it's not just a bad reading of the battery, my battery is actually being drained at these alarming speeds. I really want to like this Distro but everyday, something else hinders my ability and desire to use it.
 
So if anyone can please figure something out, pelase let us know.

---

### Post by AlesUbu123 on 2007-12-26
Using powertop advice I have managed to reach about half an hour more battery life from my new battery - still round 90 minutes less than in XP. 

Having read that users of Feisty Fawn had better battery lives, I have been trying to install Feisty Fawn on my laptop, but with no success as my graphics card was not recognised and I was left in the command line (which is not that terrible, but still...)

**I have no choice here but to ask if anyone knows a more economic (in the sense of battery life) distro for me to use. **

It is not just the battery - but in my opinion when something uses so much more power for same tasks there must be something wrong with it in general - more CPU cycles or more accessing my disks, etc probably means reducing the lifetime of my computer components - which is not acceptable for me:-|.

Otherwise Ubuntu rocks - of course.

Seasons greetings :)

_
Intel Core 2 Duo T5470 (1.60GHz) 800MHz FSB,  Intel GM965, 2GB DDRII memory, 120.0GB SATA HDD, Intel Graphics Accelerator X3100 (up to 384MB shared memory)

---

### Post by ahm911 on 2007-12-26
small tip i have increased my battery time by almost 30 mins when i turn some of the programs i dont need off from the systems monitor applet, and using my headphones instead of the built in speakers. man i really want gutsy to behave like fiesty.

---

### Post by AlesUbu123 on 2007-12-26
I have found this on [www.lesswatts.org](www.lesswatts.org) for those who have Intel 965GM chipset: 

> <interrupt> i915@pci

The Intel graphics driver used to have a bug where it set up the hardware to generate an interrupt (called VBLANK) each time the screen finished refreshing (typically at 60Hz or 72Hz). In normal 2D mode, this interrupt isn't actually used. PowerTOP unveiled this bug and the current Intel graphics driver no longer has this behavior.

If you're in 3D mode (for example because you are using a 3D desktop), this interrupt is currently still needed for OpenGL compatibility. We're investigating ways to mitigate this, but this is going to be a fairly invasive fix. We'll update this webpage with more information once we have this solved.

If you do not need 3D at all, you can disable DRI altogether, which will kill 3D, but also most i915-related interrupts. Simply add

  
    Option "NoDRI"


to the "Device" section in /etc/X11/xorg.conf.

It helped me a bit.

---

### Post by ElTimo on 2007-12-26
Ok the problem isn't with Gutsy incorrectly reporting battery life. Rather, it is that Gutsy simply uses more wattage than XP.

Just thought I'd get that out there.

That being said, the fact that there are laptops with integrated graphics cards experiencing this problem debunks the graphics card theory. I'm planning on trying Fedora 8 and seeing if there is any difference between kernel 2.6.22-x and 2.6.23-x. I'm not expecting there to be much, if any.

[Stop Press...err...Typing]
Looking around on the Fedora forums, I've heard mention of a so-called "laptop-mode." I know that Ubuntu has this feature because I watch it initialize every time I turn on my laptop (I hate not being root, so I usually boot in recovery mode). I dont know how to make changes to it though, so I'll have to do some digging for that.

---

### Post by ElTimo on 2007-12-26
i may have found our solution!

Look in Synaptic for a package called powersaved. Install it from there or use ```
sudo apt-get install powersaved
``` It will uninstall apmd which is fine, it won't break your system. Previously, I was getting about 2 hours and 25 minutes on a 9-cell battery, now I get somewhere around 4 hours! This was achieved using both laptop-mode and powersaved. I hope this works for others.

---

### Post by t3hi3x on 2007-12-27
were you guys using desktop effects in feisty and still in gutsy? Using the gfx cards (especially for my 7400 go) kills my battery. GFX cards are very demanding on the amps.

---

### Post by ElTimo on 2007-12-27
Tried it with metacity, e17, flux/black/openbox, compiz fusion, and kwin/kwin-kde4, and the only difference i can remember is that turning on compositing in kwin and metacity decreased battery life, but that's to be expected since they use software compositing, which uses more CPU to do the shadows/transparency. That aside, I did notice someone mentioning that they used Vista, *shudder*, which uses graphics hardware for effects, and that they still noticed a significant hit to battery life when switching to Gutsy. It was a valid idea though.

---

### Post by greblus on 2007-12-27
I've been fighting with this issue recently (Thinkpad R61i) and that's what I've found out:

1. laptop mode is disabled by default (/etc/default/acpi-settings if i remember correctly).
2. gnome-power-manager is giving incorrect remaining battery time estimations. powertop gave me approx. 1h more and I've decided to disable gnome-power-manager. There is a gnome applet which is showing correct estimations. At least I get similar values than on Win XP and I was able to verify that it's quite correct. 
3. I've been able to gain some more minutes on battery after turning-off the wifi when it's not used (powertop will tell how to do this) and blacklisting yanta_socket (I don't have anything on pcmcia) and usb 1.0 support (there is also one module to unload, it's easy to find it on thinkwiki).
4. I believe that usb autosuspend does not work on my Thinkpad, so there are some minutes to gain.

For a "lazy staying in bed with jabber+slrn" i get around 4 hours. More productive work is approx. 3h40m but as I wrote, there is still something to turn off ;).

Hope this helps.

---

### Post by AlesUbu123 on 2007-12-27
I have also tried running Ubuntu with IceWM and all desktop effects disabled and no difference in battery life.

> 1. laptop mode is disabled by default (/etc/default/acpi-settings if i remember correctly).
Laptop mode is really disabled by default. Enabling it got me quite a few minutes time indeed.(/etc/default/acpi-support). \\:D/ Hope I don't have troubles with disk spindown destroying my laptop hard drive [(Bug 59695)]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")

> 2. gnome-power-manager is giving incorrect remaining battery time estimations. powertop gave me approx. 1h more and I've decided to disable gnome-power-manager. There is a gnome applet which is showing correct estimations. At least I get similar values than on Win XP and I was able to verify that it's quite correct.
Also true, if I am unsure I check battery status in the CLI with "acpi -b".

> Look in Synaptic for a package called powersaved.  
Installing this caused the removal of powernowd, which disabled the CPU scaling function which would actually decrease the performance of my battery. (my  CPU was at maximum freq all the time!) :roll: Or have I done sth wrong?

I also got some minutes by turning off bluetooth according to powertop suggesstions.

Regards,
Ales

---

### Post by greblus on 2007-12-27
> Laptop mode is really disabled by default. Enabling it got me quite a few minutes time indeed.(/etc/default/acpi-support).  Hope I don't have troubles with disk spindown destroying my laptop hard drive (Bug 59695)

That's an interesting thing, I don't fully understand how it's related to Linux ;) the only explanation is that there are some workarounds for this under Windows and... hard drive manufacturers are greedy, not to say something worse.

I've read through the bug report only to estimate, that at the current rate of load cycles per hour my hard drive (Fujitsu) should work more than 6 years... I believe it's enough, but thanks for pointing this out, it looks really scary.

The only thing that I've changed was SPINDOWN_TIME, as with the default value of 12 (IIRC)  the hard drive turns on and off way to often.

---

### Post by AlesUbu123 on 2007-12-28
Well,
I have now decided to just stick to XP when running on battery... It seems funny how I am struggling for 3,5 hrs on ubuntu and XP easily gives me 5 hrs of remaing time. 

Any other advice (or logical explanation) would be very much welcome :D

Regards,
Aleš

---

### Post by katakaio on 2007-12-28
> **AlesUbu123 said:**
> I have found this on [www.lesswatts.org](www.lesswatts.org) for those who have Intel 965GM chipset: 



It helped me a bit.

I have also done nearly everything I can think of to prolong battery life. In fact, I did most of the watt-saving mods under Feisty, including laptop mode, processor scaling with powernowd (similar to ElTimo's powersaved), etc. Again, this thread isn't about how to save battery life - there are plenty of threads and FAQs about that. We're trying to figure out what happened with Gutsy that caused such a drastic loss in battery life, independent of hardware.

However, if powernowd or powersaved are news to you, the I highly recommend trying them. Hopefully it will work as well for you as it did for ElTimo. But if you're still missing some battery life from a Feisty or XP configuration, then we'll take it from there.

The two things that are new with Gutsy are Compiz and the tickless kernel. Do any devs or handy coders know much about these additions and how they could possibly result in less battery life? Thanks again everybody!

---

### Post by AlesUbu123 on 2007-12-29
For those interested, I have found three pages that returned my optimism for better power efficiency when on linux:

1. In contrast to my first impression, Ubuntu developers are obviously aware of this problem, so here is an account of what should be done in future:
[Power management in Ubuntu]("https://wiki.ubuntu.com/power-management-in-Ubuntu?highlight=%28power%29")

2. This is a guide of few maneuvres to save battery in ubuntu:
[Reduced power usage in Ubuntu]("https://wiki.ubuntu.com/ReducedPowerUsage?highlight=%28power%29")

3. Probably most complete overview of things you can do to reduce power use on a laptop with linux:
[How to reduce power consumption]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption")
Hope it gets you at least 30 minutes more batt like in my case :)

Regards,
Ales

---

### Post by goofygrin on 2007-12-29
I just install Gutsy on my E1505 and was noticing a very quick battery drain.

There are three things that made the biggest difference for me.  In fact, now my battery life is greater than the clean XP install on my other partition!

1. laptop mode
2. turn off bluetooth (I don't have a bluetooth module anyway) and other misc unneeded drivers/services
3. turn down the LCD.  Once I looked away it became less of a problem

I also conditioned the battery/Gutsy by letting it run all the way down and die (and it was at like 5% for a LONG time).  That seemed to help quite a bit too.

---

### Post by ahm911 on 2008-01-04
i agree with goofy i noticed two things first activating laptop mode with cpu freq added a whopping 50~60 mins with lcd 90% dimmer.

also the power applet always miscalculated my times it would still say 1hr 40 remaining on a full charge but when i used " acpi -b " i would get 2hrs 55 remaining and that was true as i used it at my buddies listening to music with the screen on and internet on it followed the numbers in the acpi command and the power applet would get erratic at the end.

---

### Post by dtwwtd on 2008-01-04
I have a Dell Vostro 1500 and I notice the same thing.
In Vista there is an estimated 4.5 - 5 hours of battery while in gutsy the highest I can configure it to get is about 2:45 hours.

Core 2 Duo 1.6Ghz, 1GB RAM , 128mb nvidia 8400m gs

---

### Post by AlesUbu123 on 2008-01-06
I have noticed that some other graphics cards have the option to enable the powersaving mode. Is this also available on intel graphics chipset?

Regards!

---

### Post by falonyn on 2008-01-10
[COLOR=Black]I have noticed the same thing since upgrading to Gusty Gibbon. I used to get about 3.5 hours of battery life, and I am down to 2 hours and 10min. 

Gateway MX6960 with Intel Core 2 Duo 1.83GHz, 2g RAM, Intel GMA 950

When I use acpi -b I get 2hrs and 55min at 66%, but the default power management shows I only have 1hr and 30min. 

I eagerly await some solution to this. Thank you Ubuntu community for being on top of things and providing some great power saving tips.
[/COLOR]

---

### Post by dixon on 2008-01-16
Has anyone tried other distro like opensuse if there's the same battery life?

---

### Post by AlesUbu123 on 2008-01-16
On Ubuntu - I reached 4,2 hours max, 3,5 hours on openSUSE, and about 4,0 hours on Fedora. But I have been experimenting mostly in Ubuntu, so other distro's could be tweaked to get even more out of the batt.

Has anyone actually measured the battery life on XP? I think XP could be calculating it wrong. When my battery is full, XP's show 5 hours and Ubuntu 4. But after an hour or so - it's 3,5hrs on XP and 3hrs on Ubuntu. When I have only 30 % battery remaining, ubuntu and XP show me the same remaining battery life. Weird- 

Regards

---

### Post by Elena678 on 2008-01-16
Hello, I don't know if my battery live is much or not, I have only tried this ubuntu on my laptop. I have a HP Compac 6710b bought this summer, and my battery life is something around 2 hours and 2 and a half. Is that okej?

I also fount out somthing, somethimes when i am working the el-net, and i switch to battery, the screen light is not going down, it still on 100%, i need to put it self down then, when i have that problem, my battery also lives only 1 and a half our. maybe that's a problem with some people.

greetings

---

### Post by dixon on 2008-01-16
> **AlesUbu123 said:**
> On Ubuntu - I reached 4,2 hours max 
Could you please post what steps did you take to get 4,2 hours? I have also HP 6720s...

---

### Post by Elena678 on 2008-01-16
can laptop mode help this problem, i readed something about it in this treat, [http://ubuntuforums.org/showthread.php?t=607120](http://ubuntuforums.org/showthread.php?t=607120)

i did not installed it yet, because i don't know what it is doing to my laptop, see [http://ubuntuforums.org/showthread.php?p=4142281#post4142281](http://ubuntuforums.org/showthread.php?p=4142281#post4142281)

greetings

---

### Post by AlesUbu123 on 2008-01-17
> Could you please post what steps did you take to get 4,2 hours? I have also HP 6720s...

1. I emptied the battery, turned off the laptop and left it to recharge completely while turned off (though this is not a good everyday practice for the battery)
2. I have downloaded powertop and followed all its advices.
3. I have noted that the graphics adapter was waking my CPU 60 times per second or more, so I added "NoDRI" option in xorg.conf as stated on this link:  [http://www.lesswatts.org/projects/powertop/known.php#intelgfx](http://www.lesswatts.org/projects/powertop/known.php#intelgfx). 
Using this, I managed to reduce wake-ups to 20 per second. 
4. I turned off bluetooth and wake-on-lan options in BIOS. 
5. I turned of wireless.
6. I reduced the screen brightness to 20%.
7. I used laptop-mode utils. There, I enabled hard drive power saving and set the frequency governor to powersave when on battery. 

That should mostly be about it. :)
Regards!

---

### Post by dixon on 2008-01-17
> **AlesUbu123 said:**
> 
That should mostly be about it. :)
Regards!
Thanks for the tips...

---

### Post by lever1208 on 2008-01-19
I installed Gusty two weeks ago, and there are Windows xp & Ubuntu in my laptop(compaq v3162 TL-56 DDRII6671.5G Nvidia Go 6150). And I found the same problem, the battery life was eaten half suddenly! It is not only happens under  Ubuntu but also under Window. My laptop and battery is not old, it should work well.

When It is recharging, I used cmd $acpi -b :

"Battery 1: charging, 73%, charging at zero rate - will never fully charge."

I can not understand why it says "will never fully charge"

cmd:
$ cat /proc/acpi/battery/BAT0/info 
get:
present:                 yes
design capacity:         4000 mAh
last full capacity:      1225 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 60 mAh
design capacity low:     42 mAh
capacity granularity 1:  18 mAh
capacity granularity 2:  1165 mAh
model number:            Primary
serial number:           
battery type:            LION
OEM info:                Hewlett-Packard 

the "last full capacity" becomes smaller! 

What happens? It seems that some values in system was changed incorrectly, because the "last full capacity" is much smaller than "design capacity".


I used lots of methods that other member offered, but it still does not work.

---

### Post by AlesUbu123 on 2008-01-19
> I can not understand why it says "will never fully charge"

Other people have been reporting this, but most have noted that their battery is being recharged anyway (despite acpi -b saying that it's not recharging). Have you tried checking battery charge % a few minutes later. Does it increase?

 I have found these links for you
[http://bits.sid3windr.be/tm8000/#acpi](http://bits.sid3windr.be/tm8000/#acpi)

[http://ubuntuforums.org/showthread.php?t=560866](http://ubuntuforums.org/showthread.php?t=560866)

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/42832](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/42832)

Regards.

---

### Post by PriceChild on 2008-01-19
Battery life is shortened by use.

---

### Post by lorebett on 2008-02-03
> **AlesUbu123 said:**
> 1. I emptied the battery, turned off the laptop and left it to recharge completely while turned off (though this is not a good everyday practice for the battery)
2. I have downloaded powertop and followed all its advices.


Hi

I've just started using powertop but one thing is not clear to me: when you follow its advices, they are not permanent right?  One should make them permanent by putting them into a script to be run when running on batteries, am I right?

---

### Post by kansei on 2008-02-03
> **lorebett said:**
> Hi

I've just started using powertop but one thing is not clear to me: when you follow its advices, they are not permanent right?  One should make them permanent by putting them into a script to be run when running on batteries, am I right?

correct. They are not permanent changes.

write them down as they pop up and then see which ones help you without unwanted side effects.

---

### Post by lorebett on 2008-02-04
OK

then I should put these commands in a script that is run when running on batteries is detected right?  But I should also put the inverse commands in a script that is run when running on ac is detected...

any suggestions or example scripts?

thanks in advance
Lore

---

### Post by TenPlus1 on 2008-02-04
Goto this site: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and get hold of the Ubuntu Tweak program and install...

It'll give you options for your processor to use full-speed when connected to AC or a user-defined setting when on Battery...  This'll help preserve battery life...

---

### Post by hardyn on 2008-02-04
I have had a quick look though, while i have been travelling and have not been able to use gutsy all that much before leaving there are a few things from my experiece.

laptop mode has never been enabled by default on any ubuntu... enable it, it helps alot; but change the hard disk cycle rate.  (two files must be edited)

power management from the video drivers is terrible; i can really only speak from an nvidia experience but NV is horrible, NVIDIA is a little better, but still seems to be designed for desktop use and does not employ the same throttles that the windows driver does.

gutsy also uses the eye candy be default... this with an unmanaged video drvier will use a whole lot more electrical resources, gpus are not currently designed to be efficient in the same manner as cpus are, disable compiz-fusion

perhaps somebody with more kernel / driver knowlege than i can shed some light whether or not intel treats the laptop video chips any differently than the desktop in terms of battery management.

ubuntu (and i don't know if any linux) does not use the power saving features that are available in the intel wireless (and i assume others) drivers.  this is a real shame.  smattered around this forum are some scrips that can be hacked into the system, but this is something that really should be available by default as the event triggers are available

when i return from travelling, i would be really interested in collaboration with some people on some of these power issues (if they arn't repaired by the time i return), its not a area i know much about, but the best way to learn is to get in there and break stuff.

cheers.

---

### Post by kansei on 2008-02-04
> **TenPlus1 said:**
> Goto this site: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and get hold of the Ubuntu Tweak program and install...

It'll give you options for your processor to use full-speed when connected to AC or a user-defined setting when on Battery...  This'll help preserve battery life...

you don't need any apps at all to have it do speed scaling on laptops. Mine does it whether or not it's plugged in. Running at full speed (2ghz) when on AC would mean it'd be sitting there with the fan running all the time creating all sorts of heat.

---

### Post by TenPlus1 on 2008-02-04
THat's not what I meant...  The full speed refers to when you NEED to use the CPU at full speed for apps etc, otherwise you can use the scaling meter to cut it down to a max of 30,40,50% cpu to save power...

---

### Post by meg23 on 2008-02-04
Some ways of saving power:

ACPI - make sure it is enabled in the configuration file

CPU Scaling - there is a kde program called kpowersave that does a damn good job even on gnome. It will automatically scale your CPU when its unplugged along with a bunch of other settings. 

powertop (sudo apt-get install powertop) - "sudo powertop" will offer you suggestions for saving power along with executable solutions from the terminal.

Graphics Card Underclock for Nvidia graphics card (sudo apt-get install nvclock) - I have never heard anyone talk about this but on my laptop it saves some power and keeps the GPU a little cooler. Sample underclock script: nvclock -n 125  -m 200 -f .

Turning down screen

---

### Post by mate0x on 2008-02-04
I am running an i700m (integrated graphics, cpu scaling set to conservative, enabled laptop mode) and my battery life is about 45% of what it should be. 

acpi currently reports :

discharging, 26%, 01:18:00 remaining

gpm shows me :

26%, 25 minutes remaining

in about 30 minutes my laptop will just die, and acpi will correctly report 0% 00:00:00  as I have been doing some diagnosing, anyone figure anything out yet? 

Downloading Hardy A4 iso right now, will report back.

---

### Post by mate0x on 2008-02-04
Well for now Hardy is a bust with the battery. GPM is buggy and listing two batteries both discharging...the one shown that i know to be "more correct" is still draining like it was in gutsy. So who knows. acpi is telling me what i want to hear...sort of.

for every % it's 3 minutes of battery life...only problem is it goes down a % every 1.5 minutes...weak.

Just an FYI incase anyone reads this, and it's not fixed, the visual effects (aka compiz) under Hardy really slows down some apps, so if your playing around with it, go into appearances and set visual effects to none. 


I really do not want to downgrade to fiesty, looks like i'll be hitting up slack/gnome for a while until this battery issue is resolved. 

Hopefully someone comes up with something :-) good luck all

---

### Post by mate0x on 2008-02-04
welp half an hour later i'm still on battery....i rebooted acpi still reads 0% but gpm has 1 laptop battery at 100% and the other battery on ac power... lol....this is getting fun. (still in hardy)

---

### Post by katakaio on 2008-02-05
> **mate0x said:**
> Well for now Hardy is a bust with the battery.

I really do not want to downgrade to fiesty, looks like i'll be hitting up slack/gnome for a while until this battery issue is resolved. 

Hopefully someone comes up with something :-) good luck all

Thanks mate0x - I just torrented Hardy A4 hoping that it could be the magic bullet, but now I won't bother with it. I appreciate the testing and reporting on it. (And I also appreciate the fact that I'm not the only one considering a downgrade to Feisty!) If you find any more interesting twists and turns with Hardy, please let us know.

I don't want to come off as a jerk, but here goes. A lot of posts in this thread deal with powersaving techniques and utilities. This is not the purpose of this thread - here we're trying to solve the halving of battery life under Gutsy that takes place regardless of powersaving practices. In fact, most of the people experiencing these problems have already implemented every available powersaving technique. I won't beat a dead horse, but I respectfully request that you do not post any tips on saving power (processor throttling, wake-ups, etc) in this thread. Those tips are strongly encouraged, but are more pertinent in another thread.

The last thing I want to do is stifle participation. (I want to do that even less than I want to revert to Feisty . . .) This thread has gotten a lot of exposure and received a ton of wisdom. Keep up the good work! I think we'll beat this problem yet!

---

### Post by mate0x on 2008-02-05
Just for kicks....

I just finished a feisty install and the acpi and gpm both report 5 hours remaining on my battery. I will let her drain down and report back just to prove it's not actually the battery that is the problem.

side note: i used unetbootin to install feisty from the net with out any installation media and it works fantastic A++++ to everyone who worked on that.

---

### Post by kansei on 2008-02-06
I got 4 hours of battery life with gutsy (and hardy).. and 4 hours on Debian Lenny (testing). It's not isolated to Ubuntu.

Windows gets 7 hours (not that I use windows.. I just have a hard drive with an old windows xp sp2 install that I checked with to make sure the new battery wasn't worn down already)

---

### Post by mate0x on 2008-02-06
Well now I dont know what is going on because feisty last night didn't improve the battery life, have they included a newer kernel in feisty than when I previously had it installed (been a while, I had to kick back to winblowz and was on AC power for a while, no need to be mobile)... is this a kernel issue?? Haven't been able to test on windows after this discovery, but i remember it to be fine, hopefully it's not actually my battery....that would be a terrible coincidence. Guess I'll throw XP on tomorrow and see whats what.

What would we do if it was a kernel issue....revert? recompile with older/newer/without dynaticks? (sorry i know i spelled that wrong)

Hopefully something comes up.

---

### Post by lorebett on 2008-02-07
Hi

Just a quick experience report (I'll do some more tests in the near future): with the extended dell battery under windows I get more than 6 hours (approx.) while under (k)ubuntu I get less than four hours (effective).

I did some tweaks with laptop-mode, lm-profiler and powertop... however, what really seems to make the difference is setting the CPU policy to powersave, instead of dynamic: this seems to give me about 6 hours... \\:D/

hope this helps

Lorenzo

---

### Post by zgoda on 2008-02-08
> **lorebett said:**
> I did some tweaks with laptop-mode, lm-profiler and powertop... however, what really seems to make the difference is setting the CPU policy to powersave, instead of dynamic: this seems to give me about 6 hours...

But isn't powersave sticked to lowest available frequency? Anyway, thanks for the tip, I'll check if 800MHz will be enough for me... ;)

---

### Post by lorebett on 2008-02-09
> **zgoda said:**
> But isn't powersave sticked to lowest available frequency? Anyway, thanks for the tip, I'll check if 800MHz will be enough for me... ;)

yes, it sticks to the lowest freq, but I think this is what windows does to give you so much more battery time, and I found that this is what really makes the difference in linux too.

---

### Post by Whiffle on 2008-02-10
Will someone post up a kernel config for gutsy for me?  I don't have it on my computer and I'm curious what kernel options its got.  I just did some compiling and such on my feisty equipped T43, and got it from ~17 watts at idle with the (nearly) stock kernel (hdaps added on), to 13-14 watts at idle, which is almost exactly what windows uses (and i think there is still room for improvement).  Thats with the latest kernel from kernel.org.  I'd like to compare my config to a gutsy one and see if I can find any glaring differences.

---

### Post by pbenway on 2008-02-10
I have noticed there are two different options for panel info on battery status, one icon that is activated from Power Management Preferences and one panel program to survey battery charge (I'm sorry if I don't use the correct terms for these things, but I'm new to Linux). I get different values from these two sources: The first (the icon) says my battery will last 50 min, the second (the panel program) says I have 1h 45 min to go. Both give the same percentage of battery charge (96%). I haven't tested which one gives more realistic approximation...

(I run a Toshiba Satellite u300-11z)

---

### Post by katakaio on 2008-02-12
> **kansei said:**
> I got 4 hours of battery life with gutsy (and hardy).. and 4 hours on Debian Lenny (testing). It's not isolated to Ubuntu.

> **mate0x said:**
> Well now I dont know what is going on because feisty last night didn't improve the battery life

What would we do if it was a kernel issue....revert? recompile with older/newer/without dynaticks? (sorry i know i spelled that wrong)

Those are really interesting results, guys . . . if Feisty got an upgraded kernel and still gives us problems, and if current releases of Debian are posing the same problem, then the issue isn't Gutsy specific - it has to do with the kernel! Probably no coincidence that this kernel is the first to incorporate dynticks . . . is there a way to get a kernel without the dynticks "upgrade"?

I feel better that it's not a Gutsy problem, and I think we've isolated the issue. Now, who knows where we can find a dyntick-less kernel?


Edit: Maybe this could get us on the right track . . . from [http://www.lesswatts.org/projects/powertop/faq.php](http://www.lesswatts.org/projects/powertop/faq.php)

[I]Why did my power usage increase with dynticks? Why do I never reach sleep states deeper than C2?

The current ACPI sleep function requires wakeups to reach deeper sleep states. Certain drivers, such as ipw2200, limit the initial sleep state to C2 due to DMA activity. With dynticks, which tries to sleep as long as possible, this means that your processor will, most of the time, only reach C2 and thus waste power compared to a non-dynticks kernel if it is mostly idle. This will be solved by an upcoming cpuidle patch. Until this hits mainline, you should compare your power usage with and without dynticks (and maybe with different HZ values) to figure out which is currently the best for your workload.[/I]

---

### Post by Whiffle on 2008-02-12
My kernel (2.24.2) is using dynticks (pretty sure its CONFIG_NO_HZ) in the config file, and I can get my T43 down to 13 watts that way, with an estimated ~3.6 hours of battery life on my 6 cell 51840mwh battery (im kind of guessing there, I never actually charge my battery  full anymore, max I charge it is 85%, which is where powertop shows 3.1 hours )

The biggest power drain for me  wireless and hard  drive, which can easy cost 1-1.5 watts each...

---

### Post by clarious on 2008-02-12
Hello, I am having problem with battery life on Ubuntu Gusty Gibbon too. But I have found that Kubuntu have much better battery life.


I have a Dell Vostro 1500 with 6 cells battery and I get around 4 hours and 30 minutes under windows (idling, with monitor on) and with normal usage(web browsing, reading, music) the battery will last for about 3.5 hours. While with Ubuntu, the battery life is much worse, idling -- 2.75 hours and around 2 hours under normal usage. :(

The interesting thing is after installed kubuntu(via synaptic), the battery life is the same as on windows, idling = 4.5 hours. And I can get 3+ hours working with my laptop (turning off C3 mode for lower noise in headphone, turning off power managerment on my HDD, I don't want it to die soon). :KS

---

### Post by linuxisfree on 2008-02-12
I actually have the same problem. When i was using Feisty my Laptop usually game me about 5 to 6 hours of life... but when i switched to Gutsy, i lost about 1 to 1 and a half hours worth of battery life. What gives?

---

### Post by Whiffle on 2008-02-12
> **clarious said:**
> Hello, I am having problem with battery life on Ubuntu Gusty Gibbon too. But I have found that Kubuntu have much better battery life.




There might be something to this actually.  According to lesswatts.org, gnome-power-manager is a program that is bad to have running when you went good battery life (ironic, eh?).  


[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)

---

### Post by fabbaz on 2008-02-14
i have a macbook c2d running feisty:
at first i installed gutsy, had the horrible battery life (about 2 hours max with wifi and bluetooth and screen backlight nearly off. After reading this thread tried feisty clean install, everything worked: and the battery was in normal usage up at the 3.5 hours i was used to have in mac os x.
well, yesterday's automatic update brought a new kernel header and some other "critical" updates......

at first i thought they had only broken my wifi, which they had. but i repaired that already by reinstalling the madwifi drivers. (and then, i don't know why, after 2 reboots, it suddenly started working again)
but guess what else happened. i'm back to good old 2 hours maximum battery life.
i mean: what the duck. why would an automatic update break something? that is something i am only used from working with windows.

long story short: if you downgraded to feisty because of the problems described in this thread: for christs sake don't "update" the kernel.

if i don't find a solution on downgrading that update i guess i'll have to reinstall the whole laptop all over again.

i am so frustrated with this. if there is anything i can do to help fix this problem, please tell me what to do.

---

### Post by am7146 on 2008-02-15
I have a similar problem.  I went from Feisty to Gutsy and saw my battery life cut waaay down.  I installed PowerTop and am seeing a lot of wakeups.  Usually around 4k/sec after taking it's advice on the common things.

```
     PowerTOP version 1.8       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 9.3%)         1.60 Ghz     2.6%
C1                0.0ms ( 0.0%)         1400 Mhz     0.0%
C2                0.2ms (90.7%)         1000 Mhz     2.6%
C3                0.0ms ( 0.0%)          600 Mhz    94.8%
C4                0.0ms ( 0.0%)
[COLOR="Red"]
Wakeups-from-idle per second : 3820.0[/COLOR]   interval: 3.0s
no ACPI power usage estimate available

Top causes for wakeups:
  61.5% (334.3)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  11.0% ( 59.7)       <interrupt> : ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, eth0, radeon@pci:0000:01:05.0 
   8.0% ( 43.7)              Xorg : schedule_timeout (process_timeout) 
   6.3% ( 34.0)       <interrupt> : yenta, yenta, wifi0, ALI 5451 
   4.8% ( 26.3)              Xorg : do_setitimer (it_real_fn) 
   2.6% ( 14.0)       firefox-bin : futex_wait (hrtimer_wakeup) 
   2.1% ( 11.3)      S20powernowd : queue_delayed_work_on (delayed_work_timer_fn) 
   1.0% (  5.3)    sensors-applet : schedule_timeout (process_timeout)
   0.5% (  2.7)       <interrupt> : acpi
   0.4% (  2.3)    gnome-terminal : schedule_timeout (process_timeout)
   0.2% (  1.3)    wpa_supplicant : schedule_timeout (process_timeout)
   0.2% (  1.0)    NetworkManager : tg3_open (tg3_timer)
   0.2% (  1.0)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn)
   0.2% (  1.0)            dhcdbd : schedule_timeout (process_timeout)
   0.2% (  1.0)         nm-applet : schedule_timeout (process_timeout)
   0.1% (  0.7)       gnome-panel : schedule_timeout (process_timeout)

```

Yes, I was touching the touchpad when I did that measurement, but even all quiet with no apps running it's over 3k wakeups.

Another thing is under Feisty I put "noacpi" in the kernel line in grub to turn off acpi--it was giving me a weird problem on my Compaq nc4010 laptop where the machine would hang and the fans would spin up then it would spin down and the machine would resume.  Turning off acpi fixed the hiccup and battery life was fine.  Now the noacpi doesn't seem to be an option in the kernel.  Not sure if it's related or not.

Battery life went from 2-3 hours to under 1 hour....

Any ideas?

Andy-

---

