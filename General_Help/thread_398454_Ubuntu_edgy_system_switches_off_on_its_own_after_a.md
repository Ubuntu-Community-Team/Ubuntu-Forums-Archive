---
title: "Ubuntu edgy system switches off on its own after a period of inactivity"
date: 2007-04-01
forum: General Help
---

### Post by saurav on 2007-04-01
Hi All,

My Ubuntu edgy PC switches off automatically if left on for sometime. The system is not shutdown as when I restart the system, I can see messages like filesystem is not clean. Windows XP in the same PC doesn't have the same problem. How can I can go about debugging the problem?

Thanks in advance,
saurav

---

### Post by acormack on 2007-04-01
if you leave it how long does it take to switch off?

does it always do it?

if you keep using it does it work ok?

when it does this does the system shutdown or does it reboot?

---

### Post by slayerboy on 2007-04-01
this sounds like a screensaver you're running is crashing X.  Try changing screensavers and see if that resolves the issue.  Might be that you're trying to run a screensaver that won't work on your graphics card.

---

### Post by InuyashaDuelist on 2007-04-01
Are you sure it's crashing? Maybe it just went into power save mode. Try moving the mouse.

And yes, this is a possibility. My friend actually ran into this problem, and so did I when I first ran Ubuntu and didn't realize there was a power-save mode.

---

### Post by saurav on 2007-04-01
If I left it on, it always switches off (though it has started recently). I usually keep the PC on to download something but invariably find it off after some time. It probably switches off pretty quickly (after 5/10 mins) as the download doesn't progress very much. Only once I found it switching off when I was actually doing something.

The system doesn't shutdown or reboot - it simply switches off (no leds glowing in CPU, monitor turns blank, monitor led goes amber). It cannot be a screensaver/X problem as keys like CAPSLOCK on/off doesn't blink the led.

---

### Post by saurav on 2007-04-01
I also thought initially that it is getting suspended. How can I confirm that is the case. How can I resume the machine if it has gone into sleep? I cann't find any such key in the keyboard ( I have tried pressing all of them).

---

### Post by acormack on 2007-04-01
I think you need to look in /var/log/syslog to see what messages are displayed at the time it does this.

---

### Post by slayerboy on 2007-04-01
IMO if it was suspending the keyboard keys would light up when you pressed caps lock...you'd notice it turning on.

I suspect there is some kind of power issue or something of that nature going on.  But if it doesn't do it in XP then there's got to be something that Linux is doing that causing this to happen.

What happens if you create a new user and stay logged in for a while?

---

### Post by saurav on 2007-04-01
The system actually switched off between now and my last post. I have checked /var/log/syslog but I cannot find anything unusual. I'll create another user and see what happens with that user.

---

### Post by saurav on 2007-04-01
I created a new user and logged on but the system switched off even as I was opening some program. Now I have logged on Ulteo (based on Ubuntu too) to see what happens.

---

### Post by acormack on 2007-04-01
It sounds more and more like a hardware issue.

Are you sure it doesn't do this in windows also?

Have you tried running memtest of the live cd?

---

### Post by slayerboy on 2007-04-01
I have a feeling it's hardware too.  I've had systems that had hardware problems that didn't show up in XP but showed up in Linux.  It's unusual, but sometimes it does happen.

What happens when you run Ubuntu from the live cd?  Does it do the same thing?  How about from Ulteo?

---

### Post by flossgeek on 2007-04-01
Have you tried going to System>Preferences>Power Management. In the "**Running on AC**" tab ensure bars are moved so **never** displays. In the "General" tab where it says "**Sleep type when inactive**" select  "**Do nothing**".

---

### Post by saurav on 2007-04-01
Power Manager settings are ok. But I have found that the same problem is there with XP also so something is wrong with the hardware. I have tried changing the RAM but the result is the same. I wonder what else could be wrong.

---

### Post by flossgeek on 2007-04-01
Its a hardware issue then by sounds of it, you could try updating your bios firmware.

---

### Post by acormack on 2007-04-01
If you have more than 1 memory stick (dimm) I would try taking one out.

If that doesn't help try taking the other out.

If you have only got 1 dimm then I would try taking it out and re-seating it.

Then run memcheck from the live cd.

---

### Post by slayerboy on 2007-04-01
I'm thinking it might be the CPU overheating. Does the CPU fan spin when youturn the computer on?  If you leave the case open, watch the fan while you have it on.  It might stop after a minute or so or not even turnon at all.

I'm not so sure it's memory because usually memory is related to lockups and freezes, not really the whole system shutting down.  CPU overheating or problems with the power supply will cause this.

---

### Post by saurav on 2007-04-02
The CPU fans are working but the heatsink seems to be very hot. I have a single DIMM. When running memetest also the system switches off after sometime. But the same RAM is working on another PC.

---

### Post by slayerboy on 2007-04-02
If your BIOS has the ability to display system temperatures, get into the BIOS and watch the temps while you leave the computer on for a whle to see if anything happens while you are in the BIOS only.

As long as the is moving, there shouldn't be a problem.  Average temp of my CPU is around 120-130 degrees Fahrenheit and the Motherboard is usually 90 degrees.

If after say an hour of leaving the system on in the BIOS and not having it shutdown, then we need to look at your hard drive, as you said the memory works fine in another computer.

That's not to say that there could be something wrong with the memory slots, but let's eliminate as much as we can before we jump to the conclusion that you need a new motherboard.  You could also do the same thing you did with the memory and try to run the hard drive in another computer to see if it crashes.

I hate to tell ya, but I think this is a motherboard issue, it looks more and more like it, but let's try testing more just to make sure.  How old is your system?

---

