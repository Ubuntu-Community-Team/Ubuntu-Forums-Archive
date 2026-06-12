---
title: "Computer is constantly shutting down"
date: 2013-12-18
forum: General Help
---

### Post by michaelcanlbel on 2013-12-18
Alright, so a few days after I had upgraded to ubuntu 13.10, my computer had shut down by itself for no apparent reason (aside from updating my OS there had previously been no changes the the hardware or software). When I rebooted it, I had noticed that one of my programs was gone/corrupt, and Ubuntu software centre wouldn't open, although thanks to the help of others I have fixed both of  those problems. Now, my computer will always shut off when I put strain on the graphics card/cpu, As in 0:30 - 2:00 into a video or even playing a computer game (Such as freerider or minecraft). I had deleted all suspicious and unused files on my computer, but when I tried to run clamTK or even a memtest, the computer would stop halfway through and shut down. It's quite possible that it's an error with my hard drive because before I changed to Ubuntu (I was running win XP at the time) the computer was having the same problem, and I had to get the hard drive reformatted/wiped. (not 100% what was the problem at the time, but it was fixed anyway). It might be possible that it's a temperature/heat related issue, but since it's been running perfectly for the past while I can't say there is a high chance of it being that.

_SYSTEM STATS:_
Motherboard: Biostar G41D3+
Processor: Intel core 2 duo @ 1.80GHz x2
Ram: 4GB DDR3 RAM
Graphics: Geforce 7200 GS

If you need any more details, just ask.

---

### Post by Bashing-om on 2013-12-18
michaelcanlbel; Hi !

Do not get to hasty in blaming the software, test the hardware 1st, as that is easy to do:
I recommend running diagnostics to check your ram (memtest), grub's boot options menu
and hard drive (smartmontools), disk utility.

Then, see what is reflected in the logs; dmesg, kern.log, and syslog for starters.

just what I would do

---

### Post by michaelcanlbel on 2013-12-18
Well I ran 2 memtests, both of which shut off the computer in under 5 minutes.
As far for everything else, It would be accurate to say that I close to no idea what I'm doing. (posting this thread in the beginners section would've been a better idea)
Anyways, I'll continue what I'm doing and I'll report back with the results later.

---

### Post by andyfied on 2013-12-18
I would still take a look at your cpu temp. It might not be the problem, but it might have just started at the same time you upgraded by coincidence.

---

### Post by Bashing-om on 2013-12-18
michaelcanlbel[
Yeah ! +1 ^andyfied .
Might see what you can do about blowing the box out ,, stabilize the cooling fans- not to allow them to spin - when you clean the box and vents,

[INDENT][INDENT]runnin' hot now is not good [/INDENT][/INDENT]

---

### Post by michaelcanlbel on 2013-12-18
Temps when simply browsing forums:
```

temp1:        +22.0°C  (crit = +127.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (high = +74.0°C, crit = +100.0°C)
Core 1:       +40.0°C  (high = +74.0°C, crit = +100.0°C)

```

When watching a video:
Temperature doesn't pass +30.°C
Core Temperature doesn't pass +50.0°C

---

### Post by 2048megabytes2 on 2013-12-18
The problem could possibly be your power supply.  You might want to test your system with a working power supply unit to see if that is the issue.

---

### Post by michaelcanlbel on 2013-12-21
tried, power supply doesn't seem to be the issue

---

### Post by Elfy on 2013-12-21
If you've run 2 memtests both of which resulted in the machine shutting down then the issue's not Xubuntu or indeed any other OS.

Have you tried removing the memory and reseating it? 

If you've got more than one memory card in there - try using them one at a time with a memtest - maybe a dodgy one.

---

### Post by michaelcanlbel on 2013-12-22
*sigh*
Yes I just attempted that (unplugged all the cords, removed both RAM sticks, put them back,) and now when I turn the computer on, the monitor and tower both power up, yet the monitor goes to sleep mode after 5 seconds (everything is plugged in, the video cable is in and the screen says no signal).
So I guess now I have a problem with my video card...

---

### Post by Elfy on 2013-12-23
well it's certainly looking like hardware

check everything in there - make sure everything is seated properly

I've had similar hardware issues - can be a pain to track down sometimes

---

### Post by michaelcanlbel on 2013-12-23
Cleaned all the contacts on everything, made sure everything was plugged in right, solved my second problem, but it once again shut off during a memtest. Slowly losing hope...

---

### Post by Elfy on 2013-12-23
I don't know - whatever it is - it's logically hardware - assuming you can get in the bios - run a memtest, let it shutoff - boot - go to bios - there should be somewhere in there you can check temps.

Other than that I'm at a loss.

---

### Post by Yellow Pasque on 2013-12-23
> **michaelcanlbel said:**
> Yes I just attempted that (unplugged all the cords, **removed both RAM sticks**, put them back)

Yes, but did you try running with just one RAM stick? If you get the same results using each stick individually, then I would rule out a bad stick (though there's still a really small possibility that both went bad a t the same time).

Some things I would look at:
- Resetting CMOS (see mobo manual)
- Northbridge heatsink (I've gotten some mobos with really crappy thermal paste that wore out quick)

---

### Post by michaelcanlbel on 2013-12-23
Did as you said, same thing happens with each ram card. Checked temperatures while watching videos/playing web games, average temps, then cpu shuts off. Might as well just take it to a computer shop.

---

