---
title: "Hook up laptop to TV"
date: 2014-10-30
forum: General Help
---

### Post by bob brazie on 2014-10-30
Ubuntu 14.10
How can I hook my laptop up to my TV to view power point type media on my large TV.

Bluetooth? Cables?

Thanks in advance. Bob.

---

### Post by David D. on 2014-10-30
What ports do you have on your laptop?

I use HDMI for this with my laptop.

---

### Post by bob brazie on 2014-10-30
Where do you hook it into the laptop and what application or settings do you use in order to get it to the cable then to the TV?
I do have two HDMI inputs on the back of the set.

---

### Post by Bucky Ball on 2014-10-30
Plug a HDMI cable into the laptop, other end into the machine. Switch the TV on. Change the input source to whichever HDMI input the laptop is plugged into. Switch the laptop on and wait. You don't need special software. It should just work. That easy, or at least should be.

---

### Post by grahammechanical on 2014-10-30
Do you have an HDMI output from the laptop? If so, then buy an HDMI cable. What video driver are you using? If it is a proprietary video driver then there should be settings utility for it in the Dash. That should have a function called Detect Displays. If we are using an open source video driver then we go to system Settings>Screen Displays and click Detect Displays there. Se what happens.

There maybe a keyborad function key (Fn) that you need to press to activate the signal output to the TV. The laptop's user manual should guide you here. As will the user manual the TV, which you need to check to see how to switch from TV mode to HDMI mode on one of those two HDMI inputs

Regards.

---

### Post by bob brazie on 2014-10-30
And if the laptop does not have an HDMI output?

---

### Post by Bucky Ball on 2014-10-30
VGA. They all have them (haven't seen one that doesn't). You can even get HDMI to VGA adapters.

But you have two HDMI ports in the laptop and I'm presuming one in the TV. HDMI carries audio as well as video. VGA does not and you will need to run a separate audio cable so go HDMI (better resolution, too).

---

### Post by bob brazie on 2014-10-30
It has the round s video and a rectangular output for a multi prong plug in. And of course USB ports.

---

### Post by bob brazie on 2014-10-30
None on the laptop but two on the TV.

---

### Post by Bucky Ball on 2014-10-30
*Thread moved to **General Help**.*

Please avoid posting in the ***New to Ubuntu*** forum as you're not. You'll find you improve your chances of support posting in the appropriate section of the forums anyway. Thanks. ;) 

You want a VGA cable, then, and you need to run sound from the headphone socket of the laptop to an amplifier (or the audio input socket of the TV, if it has one, which is unlikely, but some do). 

You have the video cable covered: VGA. Now you need to figure out how to get sound. 

I'm guessing the socket on the laptop looks like [THIS]("https://en.wikipedia.org/wiki/VGA_connector")? You will find the TV should have one, too. If it doesn't you will need a HDMI to VGA adapter.

---

### Post by JeQhdMD on 2014-10-30
So, goto Amazon and look up vga to hdmi adapter.   The vga port on a laptop is rectangular and usually blue - good luck.

---

### Post by bob brazie on 2014-10-30
Thats what i have. I think i can make it work but will not mark this as solved unill i get the parts.
Has anybody got this to work using bluetooth?
i am new to what my question  is about.

---

### Post by Bucky Ball on 2014-10-30
Bluetooth??? Does your TV have bluetooth??? If it doesn't, no, there is no way to get this working with bluetooth. Never heard of that approach, but I'm not aware of everything under the sun. ;)

Before you ask, forget doing this with USB. Your option is VGA to VGA or VGA to HDMI with an adapter (or VGA to HDMI cable, if they exist). All will need audio from the laptop headphone socket somehow. As I mentioned, that is really your concern. The vision part is/should be easy.

---

### Post by bob brazie on 2014-10-30
I was thinking of a Google Chrome TV stick.

---

### Post by Bucky Ball on 2014-10-30
> **bob brazie said:**
> I was thinking of a Google Chrome TV stick.

? What exactly are you going to do with it? Plug it into the laptop (in which case you still need to get an audio and video signal to the TV) or into the TV (which is already a TV so redundant).

If you are going to plug a TV dongle into the laptop then plug the laptop into the TV there is no point. Why not just watch the TV?

---

### Post by bob brazie on 2014-10-30
Show a power point presentation on my large tv. Just thought it would be nice to leave the laptop in the office and still be able to watch the presintation in another room.

---

### Post by Bucky Ball on 2014-10-30
Have no idea how the TV dongle comes into it. I have attached a mudmap of what you need to do cable-wise. If you only want powerpoint presentation (no audio) scratch the headphone socket to amp connection. They're about your options.

---

### Post by bob brazie on 2014-10-30
The chrome dongle goes into the tv. You haven't seen one?

---

### Post by Bucky Ball on 2014-10-30
I've got something similar, but no idea how it is applicable here is what I'm saying. You plug a TV antenae into it, right? Anyway, you want to get the signal from your laptop into the TV and I can't see how that is applicable. 

Read post 17 and good luck with it. ;)

---

### Post by bob brazie on 2014-10-30
Thank you. Much appricated.

---

### Post by bob brazie on 2014-10-30
It streams from your wi fi to the chrome dongle from sites like Netflix etc. The dongle fits into a htmi port on your tv.

---

### Post by Bucky Ball on 2014-10-30
Well, unless you want to watch things you can only get from your laptop then that will work fine. But sounds like you want to watch a powerpoint on the TV, in which case not of any use, but I am totally unfamiliar with the device so who knows? Well, at least I don't, but unless it can stream things from your laptop as well as directly from the internet then not of much use here.

If the laptop and dongle are on the same network, though, (using the same router) then perhaps it allows you to set up a connection to your files on your laptop via the router. Research.

---

### Post by SeijiSensei on 2014-10-31
First, some HDTVs, especially older ones, have VGA ports as well as HDMI.  I have an older Sony with a VGA port but my newer LG only has HDMI.

It looks like [Miracast]("http://en.wikipedia.org/wiki/Miracast") is becoming the de-facto standard for wireless display transfers, but [support in Linux]("http://www.freedesktop.org/wiki/Software/miracle/howto/") is still [in development]("https://archive.fosdem.org/2014/schedule/event/miracast/").  You might do better with a hardware-based solution.  At the moment it's probably easier to project [Powerpoint slides from an Android phone]("https://play.google.com/store/apps/details?id=com.microsoft.office.officehub&hl=en") to a [Miracast dongle]("http://www.amazon.com/Belkin-Miracast-Video-Adapter-Supports/dp/B00HFAEBWG/") attached to the TV.

---

### Post by Bucky Ball on 2014-10-31
Or you could go the Odroid. That is like a $60 computer which can run Lubuntu and you can connect a wireless USB dongle or ethernet cable to get it on the same network as your laptop. Just grab the Powerpoint file from your laptop over the network using Filezilla or something like it then open it on the Odroid. 

Just a thought ...

---

### Post by JeQhdMD on 2014-10-31
This will work  . . . until wireless Miracast standard is adopted by more OEM's (e.g., samsung, lg, sharp, epson, etc.)

[http://www.amazon.com/Cable-Matters-Portable-Scaler-Converter/dp/B00IDFGK1W/ref=sr_1_7?s=pc&ie=UTF8&qid=1414764191&sr=1-7&keywords=vga+to+hdmi](http://www.amazon.com/Cable-Matters-Portable-Scaler-Converter/dp/B00IDFGK1W/ref=sr_1_7?s=pc&ie=UTF8&qid=1414764191&sr=1-7&keywords=vga+to+hdmi)

---

### Post by bob brazie on 2014-11-07
I used a computer with an HDMI output and it connected after messing with the settings in display.
I had to set the TV to a lower resolution and move it to the first position.
Thanks to all.

---

