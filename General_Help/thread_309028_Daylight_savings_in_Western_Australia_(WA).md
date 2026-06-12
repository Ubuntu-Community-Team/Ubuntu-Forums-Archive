---
title: "Daylight savings in Western Australia (WA)"
date: 2006-11-29
forum: General Help
---

### Post by sabredog on 2006-11-29
I hope someone can help regarding this issue or point me to the right direction if it has been raised before.

On December 3rd 2006, Western Australia will be starting a daylight savings trial for 3 years.

In 2006/07 the period will be 03/12/06 - 25/03/07

In 2007/08 the start will be at the end of October.

[http://www.bom.gov.au/climate/averages/tables/dst_times.shtml]("http://www.bom.gov.au/climate/averages/tables/dst_times.shtml")

Will there be an update so system time will take the DST into account?

cheers and thanks

---

### Post by dcstar on 2006-11-29
> **sabredog said:**
> I hope someone can help regarding this issue or point me to the right direction if it has been raised before.

On December 3rd 2006, Western Australia will be starting a daylight savings trial for 3 years.

In 2006/07 the period will be 03/12/06 - 25/03/07

In 2007/08 the start will be at the end of October.

[http://www.bom.gov.au/climate/averages/tables/dst_times.shtml]("http://www.bom.gov.au/climate/averages/tables/dst_times.shtml")

Will there be an update so system time will take the DST into account?

cheers and thanks

Check this out:

[http://wiki.debian.org/TimeZoneChanges](http://wiki.debian.org/TimeZoneChanges)

---

### Post by sabredog on 2006-11-30
> **dcstar said:**
> Check this out:

[http://wiki.debian.org/TimeZoneChanges](http://wiki.debian.org/TimeZoneChanges)

Many thanks

I will digest that tonight.

---

### Post by delfick on 2006-12-02
> **dcstar said:**
> Check this out:

[http://wiki.debian.org/TimeZoneChanges](http://wiki.debian.org/TimeZoneChanges)

i'm in WA too....(we have a dodgy government over here :D:D) 

well i just read that......

so then, what do i do ?? :D

i'm confused.....

---

### Post by sabredog on 2006-12-03
> **delfick said:**
> i'm in WA too....(we have a dodgy government over here :D:D) 

well i just read that......

so then, what do i do ?? :D

i'm confused.....

ditto here

I read it about 4 times to no avail either :(

Be nice to fix this.

---

### Post by mike55 on 2006-12-03
Hi guys, I applied the fix as discussed in [http://wiki.debian.org/TimeZoneChanges](http://wiki.debian.org/TimeZoneChanges) on several of our 6.06LTS machines and everything seems to be working OK. In short, I found it easiest to:

1. Backup your existing zoneinfo files:
cp -a /usr/share/zoneinfo /usr/share/zoneinfo.predst

2. Copy the Perth timezone file from [http://www.ucc.asn.au/~matt/time/](http://www.ucc.asn.au/~matt/time/) to /usr/share/zoneinfo/Australia/Perth (overwrite it if prompted).

3. If you are running the graphical environment, right click on the clock and select Adjust Date & Time, then Select Time Zone... and choose Australia/Perth.

4. That should be it. Some other programs might not take the change until they are restarted, but on a desktop system a reboot will take care of that.

---

### Post by kvonb on 2006-12-03
...or you could do what any ant-fascist citizen would do:  Ignore the whole pathetic thing!

Three bloody times we had a referendum and said NO, then they go and do it anyway!

---

### Post by mike55 on 2006-12-03
Amen to that! But I think the folks at work might complain if the time on all our servers was wrong on Monday, heh.

---

### Post by delfick on 2006-12-03
> **mike55 said:**
> Hi guys, I applied the fix as discussed in [http://wiki.debian.org/TimeZoneChanges](http://wiki.debian.org/TimeZoneChanges) on several of our 6.06LTS machines and everything seems to be working OK. In short, I found it easiest to:

1. Backup your existing zoneinfo files:
cp -a /usr/share/zoneinfo /usr/share/zoneinfo.predst

2. Copy the Perth timezone file from [http://www.ucc.asn.au/~matt/time/](http://www.ucc.asn.au/~matt/time/) to /usr/share/zoneinfo/Australia/Perth (overwrite it if prompted).

3. If you are running the graphical environment, right click on the clock and select Adjust Date & Time, then Select Time Zone... and choose Australia/Perth.

4. That should be it. Some other programs might not take the change until they are restarted, but on a desktop system a reboot will take care of that.

thnx :D:D

it'll probably work....(i go to adjust date and time, and in that it says the time (21:12) but when i press close, the time says 12:14 so ye, hopefully a restart will fix that (will do later :D))

---

### Post by mike55 on 2006-12-03
Yeah, I'd try the reboot, but it might be that you're set to use UTC somewhere and that is causing issues. Did you try clicking one of the options to synchronize time with an Internet server, available from Adjust Date & Time dialog?

Without knowing more about how your PC is setup (dual/multi-boot? BIOS set to UTC?), I wouldn't want to suggest changing anything else in case it breaks something ... Having said that, if you only have Linux on your machine, you might try right clicking the clock, then selecting Preferences and toggling the Show UTC button ...

---

### Post by delfick on 2006-12-03
> **mike55 said:**
> Yeah, I'd try the reboot, but it might be that you're set to use UTC somewhere and that is causing issues. Did you try clicking one of the options to synchronize time with an Internet server, available from Adjust Date & Time dialog?

Without knowing more about how your PC is setup (dual/multi-boot? BIOS set to UTC?), I wouldn't want to suggest changing anything else in case it breaks something ... Having said that, if you only have Linux on your machine, you might try right clicking the clock, then selecting Preferences and toggling the Show UTC button ...

thnx....i right clicked on the time, clicked preferences and unchecked "Use UTC" and now it works :D:D

---

### Post by sabredog on 2006-12-03
Thanks for the help everyone.

I will give this a go when I get home from work. I assume this fix will work in Edgy as opposed to Dapper?

Incidently IT has not rolled out the patch for any of our work PC's....

Oh well....

---

### Post by skylark on 2006-12-04
Does anyone know if an update will be released so I dont have to manually fix the timezone file?

Of course the fault really likes with the WA government for imposing this on us at short notice and without a referendum.

---

### Post by kvonb on 2006-12-04
Great, so now I missed Mythbusters because of this lousy fascist government diktat!

Anyone want to form a political party to overthrow these self-serving fat scumbags?

---

### Post by delfick on 2006-12-04
> **skylark said:**
> Does anyone know if an update will be released so I dont have to manually fix the timezone file?

Of course the fault really likes with the WA government for imposing this on us at short notice and without a referendum.

wasn't that short and the referendum is after the daylight savings........(not enough daylight for it, before the daylight savings ?? :D:D (lol))

ye, we have a dodgy government.....(i think the bell tower proved that :D)

---

### Post by sabredog on 2006-12-04
> **delfick said:**
> 
ye, we have a dodgy government.....(i think the bell tower proved that :D)

Shhhh, Ravlich is listening and she will deny this conversation ever took place! :p 

Used the replacement file last night on my Edgy install and it worked a treat.

thanks for all the help!

---

### Post by kvonb on 2006-12-04
Thanks mike55, I finally gave in and changed my machines and it works perfectly :rolleyes:.

---

### Post by cpudney on 2006-12-04
G'day fellow Sandgropers,

See also [this post]("http://ubuntuforums.org/showthread.php?p=1837334") - worked straight out-of-the-box.

Cheers,
Chris.

---

### Post by delfick on 2006-12-04
> **sabredog said:**
> Shhhh, Ravlich is listening and she will deny this conversation ever took place! :p 

lol......

someone should shoot ravlich :D

---

### Post by ozPATT on 2006-12-05
> **kvonb said:**
> 
Anyone want to form a political party to overthrow these self-serving fat scumbags?

i'm in :D

---

### Post by 3rdalbum on 2006-12-05
You guys could join Community First, and convert it from a one-issue party?

---

### Post by ozPATT on 2006-12-05
i have just spent 6 years in the UK, and they have daylight saving in WINTER cos the hours of daylight are about 8am to 4pm. THAT makes sense. 

Having daylight saving in SUMMER, in WA of all places, just makes no sense to me.. And as pointed out earlier, whats the point of 3 rferendums if you go ahead and do it anyway... 

well, thanks for the help with the clock though, working a treat. :D

---

### Post by kvonb on 2006-12-05
What gets me is that both "sides" of parliament can get together on something as ridiculously insignificant as daylight saving, but will they do anything about increasing violent crime?

There is something truly wrong with Governments today, they all seem to be telling us how we are wrong and we need to take their word that they know what's best for us.

Look at this AWB thing, what a joke!  If it was some Muslim organisation sending millions of dollars directly to Saddam they would have been crucified, and given the loyalties of the head dwarf (Howard), they would have probably been shipped to a torture camp to be dealt with and left to rot.  
But what happens?  Nothing, not one of the fat slugs gets even a telling off.


And look at all these anti-corruption bullshit things, what's the point?  All the bigwigs do is claim that they can't remember and they get a free holiday somewhere overseas till it quiets down.

Try telling that to a speed cop and see what happens!  "Oh sorry officer I can't remember driving my car, and also it slipped my mind that I had to drive within the speed limit".  That's OK sonny, here go to Bali for 6 months to recover from it!

Not bloody likely.

They lie, steal and cheat; then get away with it.  We should all take their example, I know I'm going to.

---

### Post by sabredog on 2006-12-05
> **kvonb said:**
> 
Anyone want to form a political party to overthrow these self-serving fat scumbags?

I reckon Burkie is doing that all by himself. Why that self serving moron is not in jail is any ones guess!!

According to the readme file regarding the new TZ file, it is good for the 3 year trial.

---

