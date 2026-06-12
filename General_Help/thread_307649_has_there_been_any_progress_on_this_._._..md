---
title: "has there been any progress on this . . ."
date: 2006-11-26
forum: General Help
---

### Post by Patrick-Ruff on 2006-11-26
ok well, I've been an on and off ubuntu user for quite some time.  there have been several things that have been drawing me back to Windows, here are some major things that did so . . . 
[LIST]
[*]REALLY bad battery life in Linux
[*]VERY poor ATI support
[*]lack of a good touchpad driver . . .
[*]almost nothing is streamlined, it all seems too patched togheter.
[/LIST]

the last one doesn't matter that much to me. but the first two are the major ones. I mean seriously, I get 4 hours in WINDOWS VISTA, with all the bells and whistles, there is something wrong with that picture. 

and the ATI support, well, that is just pathetic, it takes soo much tweaking to get those video drivers to /truly/ work. and trust me, I've done my fair share of tweaking with such things.

so really, what I want to know is if atleast the first 2 have gotten better, I have several more issues but they aren't that big of an issue to me. 

also, that third one is of interest to me as well. 

don't just leave this thread blank with no replies, it's quite simple, I'm only asking for you to answer if you know atleast something off the top of your head. 

------------------------------------------------------
here are my system specs if that helps . . . 
1.6GHz Pentium M 2MB L2 Cache
512MB PC3200 DDR2 RAM
Mobility Radeon X300 PCIe 64MB dedicated.
Intel Pro/Wireless (some number)ABG (it works fine)
Broadcom LAN card
some dialup modem that linux doesn't support at all.
15.4 LCD Screen

------------------------------------------------------

I also have some possible causes for the horrid battery life . . . there is a good possibility that because of ATI's really poor support for Linux that they hardly support mobility processors scaling and under-clocking while on battery.  just a guess though, feel free to tell me otherwise.


and that, is basically it. (sorry for the long post)

---

### Post by Patrick-Ruff on 2006-11-26
this isn't a good sign . . . not a reply so far . . .

---

### Post by RAOF on 2006-11-26
Ok.  In order:
1) I believe Edgy included some improvements for this (disabling kernel-preempt and 1000Hz clock timer).  My totally unstatistical impression is that people are pretty happy with Edgy's battery-consumption.

2) Yell at ATI.  There's **nothing** that anyone but ATI can do to help you - they don't release specs, they don't release source.  Yes, the fglrx driver sucks.  No, there's nothing we can do.

Actually, maybe there is.  You might want to try the open-source ati drivers.  It's possible that your card is old enough to be supported by their reverse-engineering.

3) No idea.

4) I don't notice the lack of "streamlinedness".  I'm not even sure what you mean by it :).  If you post some concrete examples, maybe we can say "no, that's still there" or "fixed in Edgy" :)

---

### Post by Patrick-Ruff on 2006-11-27
oh well, I said the last one really didn't matter. the battery life is one of the most important ones to me, I like to be able to work longer without having to be plugged in and all that (I'm sure everyone does).  as far as the ATI thing, I was just wondering from others experience, since I don't really keep track of linux drivers and I'm on dialup so it's a bit hard to find everything I need with ease. 

perhaps the streamlineness was my own thing . . . I didn't feel like dedicating 8 hours to making linux exactly as I wanted it . . . lol.

so if anyone knwos anything else about this /please/ post ;)

---

### Post by midna on 2006-11-27
I use ubuntu daily on my laptop and I get 3.5 hours with ubuntu edgy, and 3 hours with windows. Same battery, same 100% charge. 

Ati works, just follow the guide. A pain but like he said, yell at Ati. 

Touchpad? Sorry really tired, I assume you are talking about the mouse touchpad thingamabober. Anyways, if that is it, my zt3000 laptop has one and it has a scrollbar on the right side. Ubuntu knew that somehow and it works great, not only that but it added right click functionality if I tap the bottom right corner. Tap click works great... I reall don't know what else to say.

When you say streamlined, I installed edgy, installed automatix and got what I wanted. From there I just open synaptic if I want anything else customized.

If any of this comes off as being grating, I'm truly sorry, its not meant that way at all. I just know I can be that way when I'm running on low sleep (yay college).

---

### Post by junglepeanut on 2006-11-27
I only have one significant way of talking about battery life as I dont have windows anymore but I remember this. If I used XP to listen to music on the way to school my battery would die before I arrived at school or just after (as in before I made it to my office from the lot), but with Linux I average about 45 minutes left on my battery.

ATI driver: I have actually done the install for windows once, it was not fun but it worked. Under Linux I had one bad incident but it was my fault for forgetting I had killed a variable. Otherwise I find installing the driver not hard at all. I have also set up 3 or 4 ati computers for friends who wanted to try it out. I just don't think it is complicated any more, if a wall is hit it may have more to do with the mix of your monitor and ati etc. (Or sometimes lack of knowing the steps.)

Streamlined is how you make it. You can add and remove programs as you see fit to make it a small or large as you would like. 

Touchpad, I dont have any issues, but I know there is a bug for a certain type of synaptic touchpad in Launchpad.

Hope this helps.

---

### Post by Patrick-Ruff on 2006-11-27
I guess the battery life varies . . . I know that with XP on my laptop with all drivers installed I get 4 hours, easily. but with ubuntu on screen brightness ALL THE WAY DOWN it still gets 2 hours. or less, which is quite ridiculous, so something is definately not scaling here, like, really. and I hate tap clicking btw, it gets really really annoying when I'm typing something out and hten all of a sudden I snap to the middle of my other sentence, or click out of the typing window, or some crap like that lol. 

I know theres always the MaxTapTime "0" thing in xorg.conf, but I'd rather not have to go through that every time, I want to be able to raise the sensitivity of the touch pad, and all that other cool stuff.

is it possible that we could somehow hack up a windows driver for that?   

anyways, the streamlined thing is a bit of a personal preference thing, linux doesn't seem so built-together as say, OSX. and it's really hard to get a very good looking GUI on there, I mean sure theres XGL/Beryl, but I couldn't ever seem to find a top and bottom panel that actually looked good. 

I guess my expectations are high, but I've literally tried all the OS's, kinda lame that Mac OS X is the best out of all of then in exclusion to compatability of course. (no I don't want to start a debate thread.)

eitherh way, in my experience, those ATI drivers have been a PAIN  on linux, moreso then windows, windows you just run the bloody installer and it /works/ it doesn't crash or any of that other crap. I recall it took me over a month to get my ATI drivers /really/ working. I was trying to get XGL/Beryl working at the time, but I always had this feeling that my card was never working up to it's full potential (a video driver problem) and it wasn't. and to this day I'm still not quite sure if I ever realyl got it working, some people think it's as simple as saying glxinfo or fglrxinfo but it isn't, it /really/ isn't.

anywyas, I have better things to do at this early hour, I'll be back on later.

---

### Post by deanlinkous on 2006-11-27
uh it sounds like you want windows. When there are a few things in linux that you aren't willing to work around or tweak or accept as a tradeoff for other things it usually means you should stick to windows since you will always be looking at what Linux can't do instead of what it can do.
Try looking at what windows cant do and maybe you will see it in a new light....or maybe not.

---

### Post by Rever75 on 2006-11-27
> Try looking at what windows cant do and maybe you will see it in a new light
I have to say I REALLY love that way of thinking. The only problem is I would be thinking for an awful long time, since there is so much that it cannot do that Linux can. Could not have said it better myself. 

To Patrick:
As to the battery life and Linux I have never seem to have an issue. I get the same if not more life under Linux than I do in Windows. So I guess maybe something of yours was not configured right not sure.

---

### Post by Patrick-Ruff on 2006-11-27
I think my laptop is just ridiculously touchy. like ALL the hardware is capable of scaling; video card, cpu, wireless card, etc.  (not the ram, of course) but yeah. see, the thing is, I don't need to see some light that I have already found, really.  if I wanted windows, I wouldn't be here now would I? I wouldn't be here with my 500+ posts screaming I WANT WINDOWS. no I'm not under some psychological dillusion, I know what I want however I am conflicted between sides, I suppose I just haven't really had the time to go all out with linux and tweak it like mad . . . I don't really like to spend 9 hours getting the OS just as I want, well, I don't like doing that when it screws up several times. I know it can be very rewarding.  but the battery life is easily my BIGGEST issue, otherwise everything is fine, really. 

anyways, I'm not some windows fanatic,  I just really got sick of the ineffeciency, I tried out vista, and it seems that hasn't gotten better, at all.  as I find out more information I'll probably post on this thread . . . 

thanks

---

