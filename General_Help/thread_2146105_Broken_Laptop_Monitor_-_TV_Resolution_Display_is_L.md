---
title: "Broken Laptop Monitor - TV Resolution Display is Low"
date: 2013-05-17
forum: General Help
---

### Post by freemeliberty on 2013-05-17
Hello! I am running ubuntu 12.04 and have an_ acer aspire 4530_ with a busted monitor. As this is a spare laptop I decided to connect it to an _LG-42LB5D_ TV. It works great except that it will not (always) recognize the highest resolution. Right now and most of the time under displays it shows the TV as "Unknown" and caps resolution out at 1024x768. Sometimes it does recognize as LG and goes much higher and looks way better (I don't remember the exact resolution right now but its was 1900x???) but it never stays at that setting for more than a few minutes. 
Here is what I have tried:

-Switched to mirror displays: did not solve the problem
-Disabled monitor from displays: did not solve the problem
-Installed nvidia driver: **completely disabled** the LG tv as a display. The laptop monitor is useless so I had to reinstall ubuntu and start over!

I don't know if the VGA cable I am using could be the problem (no HDMI on this laptop :'[ its looks fine anyhow) but since I am not sure I will wait to buy a new one.

Any ideas or help on a permanant fix? Thank you

---

### Post by |{urse on 2013-05-17
Not sure this helps but the max supported resolution on that TV is 1024X768 unless it's a hi definition signal (hdmi or hdtv). My advice for a permanent solution would be to replace your laptop screen yourself, it's pretty darn easy and should cost you under 100$ diy. Also, I think that model of aspire takes an LED screen with no power inverter so that makes it even easier than most.

I know that isn't what you were wanting to hear, maybe someone else will have a trick up their sleeve for you.

---

### Post by freemeliberty on 2013-05-17
Any answer is a good answer. I checked and it definitely is an HD TV and does have HDMI connections in back. Its the laptop that is older. I will take a screen shot and post it when it 'switches' again but when it defaults to 1024x768 it looks wrong, when it jumps up to 1900x??? it looks much much better, more like how it is supposed to look.

If it was my only laptop I would consider this but as its an older one I had laying around I am trying not to spend money on it. Good to know I can replace the monitor for about $100 though. I thought it would have been way more.

---

### Post by sudodus on 2013-05-17
> **|{urse said:**
> Not sure this helps but the max supported resolution on that TV is 1024X768 [COLOR=#ff0000]unless it's a hi definition signal (hdmi or hdtv)[/COLOR]. My advice for a permanent solution would be to replace your laptop screen yourself, it's pretty darn easy and should cost you under 100$ diy. Also, I think that model of aspire takes an LED screen with no power inverter so that makes it even easier than most.

I know that isn't what you were wanting to hear, maybe someone else will have a trick up their sleeve for you.

> **freemeliberty said:**
> Any answer is a good answer. I checked and [COLOR=#ff0000]it definitely is an HD TV and does have HDMI connections in back[/COLOR]. Its the laptop that is older. I will take a screen shot and post it when it 'switches' again but when it defaults to 1024x768 it looks wrong, when it jumps up to 1900x??? it looks much much better, more like how it is supposed to look.

If it was my only laptop I would consider this but as its an older one I had laying around I am trying not to spend money on it. Good to know I can replace the monitor for about $100 though. I thought it would have been way more.

See the text marked [COLOR=#ff0000]red[/COLOR]. Maybe an alternative is to get an adapter, that converts your VGA signal to HDMI, and send that signal to the TV. But it costs about half of the price of a new laptop screen, and if you need a high quality hdmi cable too, the price is getting closer.

---

### Post by freemeliberty on 2013-05-17
I tried posting screen shots of both the high resolution and low resolutions but that didn't work. Can I not post images here to show you? 

I wasn't sure if I needed an adapter because it does sometimes go to the proper 1920x1080 and recognizes the display as Goldstar Company Ltd 52" instead of unknown. Man this is weird...

---

### Post by |{urse on 2013-05-17
Yeah, maybe an adaptor will do the trick.. and if you ever do need help replacing that screen shoot me a private message, I have step by step instructions for you :)

---

### Post by freemeliberty on 2013-05-19
OK...

I am not sure if this is a permanent fix yet but I found this site:

[http://shanereustle.com/blog/force-screen-resolutions-on-ubuntu.html](http://shanereustle.com/blog/force-screen-resolutions-on-ubuntu.html)

*****
> First, you will need to generate a new modeline to use in the  configuration by passing your desired resolution and rate to cvt. I will  use 1920x1080 throughout this tutorial.
 
**cvt 1920 1080 60** 

That should return something that looks like this
 
**# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz *Modeline* "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync** 

Copy everything on the second line after "*Modeline* " and then add that as a new mode like this
 
**xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync**
*****

The only difference for me is I had to use this command in terminal to find the proper monitor name:

xrandr

the site shows it as "VGA1" but on my laptop it is recognized as "VGA-1"

This doesn&#8217;t always load automatically on system start up but when I go to display it does automatically load to the proper 1920x1080 resolution.

---

