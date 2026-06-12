---
title: "Hard drive failing?"
date: 2007-08-05
forum: General Help
---

### Post by chrisjs169 on 2007-08-05
Over the past few weeks, I've started to notice problems with this computer.  Currently it dual boots Ubuntu Feisty and Windows XP Pro, Windows being used the most (parents use this one).  A few weeks ago, I had to go to Windows' last known good configuration after it started freezing at the login screen (usernames didn't even show) until one time it said it couldn't find a system file.  Restarted the computer (still had to use last known good configuration) and it was fine.  A few days later, it showed GRUB error 16 on boot, and after a few more tries, said "disk boot failure. insert system disk and press enter".  Few more retries showed the same thing.  Waited about 30 minutes and it was fine.  The last few days, it has also shown GRUB error 18 and error 17.  The hard drive is recognized by the BIOS, and is a 250GB Seagate drive (ST3250823A).  The computer (and everything in it) is about a year and a half old, except the motherboard and CPU, which were replaced about 8 to 10 months ago (upgrades). 

Seagate SeaTools is passing everything, but are these all signs of a failing hard drive?

---

### Post by tgalati4 on 2007-08-05
It could be the power supply.  Hook up a voltmeter to a spare set of power supply leads and watch the 12V (yellow wire) and 5V (red wire) for voltage drops during boot up.  It could be that the power supply works fine with only the SeaTools running therefore giving an OK condition.  When you wake up all of the hardware on the machine during boot, the power supply could be dropping out.

You can install smartmontools to continuously monitor the disk, but I would bet that the old power supply is having problems feeding a new motherboard.

What is the brand of the machine and motherboard?

---

### Post by Gremlinzzz on 2007-08-05
[http://www.pcstats.com/articleview.cfm?articleid=1583&page=5](http://www.pcstats.com/articleview.cfm?articleid=1583&page=5)

---

### Post by amadeus266 on 2007-08-05
> **tgalati4 said:**
> It could be the power supply.  Hook up a voltmeter to a spare set of power supply leads and watch the 12V (yellow wire) and 5V (red wire) for voltage drops during boot up.  It could be that the power supply works fine with only the SeaTools running therefore giving an OK condition.  When you wake up all of the hardware on the machine during boot, the power supply could be dropping out.

You can install smartmontools to continuously monitor the disk, but I would bet that the old power supply is having problems feeding a new motherboard.

What is the brand of the machine and motherboard?

Good place to start but simply getting the voltages isn't enough. Depending on how much hardware you are powering your PS may be under the needed watts. I wouldn't recommend any less than a 400 watt power supply to anyone. I deal with old computers all the time that were originally sold with inadequate power supplies and they exhibit all kinds of strange behaviors that are immediately solved by installing a larger power supply.

---

### Post by Wim Sturkenboom on 2007-08-05
If there have been no recent hadrware changes (as OP indicated), it can only be the PSU if it's dying.

@amadeus266:
The effect of an underpowered power supply IS a significant voltage drop as the voltage drop over the output resistance of the power supply increases due to the requested current that the power supply was not designed for.

---

### Post by chrisjs169 on 2007-08-05
It was a custom built computer, motherboard being a Gigabyte GA-81865GME-775.  

In the past, I thought I was having problems with the power supply, and took it to a repair shop a few minutes away.  That was maybe five or so months ago though.  I had told the people at the repair shop that it seemed that my computer was 'restarting' after it was idle for a few minutes - it sounded like something (fan or hard drive?) was starting up again, and the HDD activity LED was on solid for 15 seconds or so.  They also said it could be the PSU, but they tested it, and it was fine.  The power supply is 400 or 450 watts (I can check to see which if needed) and is about a year and a half old.

I'm running chkdsk on the computer now.  The only hardware change to the computer was swapping DVD drives, after the laser in one suddenly stopped working (tested it in another computer as well)

---

### Post by tgalati4 on 2007-08-05
Some simple things to check are the hard drive cable and power leads.  I have had them vibrate loose over time.  Try a different ribbon cable and a different power lead.  Could be as simple as a cold solder junction inside the power supply that is not letting enough current through.

---

