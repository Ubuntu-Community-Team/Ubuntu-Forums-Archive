---
title: "Lose of Power, What's affected?"
date: 2007-12-26
forum: General Help
---

### Post by shane2peru on 2007-12-26
Ok, let me explain, I live in Peru where the power is not stable.  I have a stabalizer to help regulate the amount of power to  a stable output, however sometimes the flow of electricity dips so low that the stabalizer can't keep it's stable flow and everything shuts off and comes back on.  As a result using my desktop computer it gets shutoff about once every 2 weeks as if someone just pulled the plug reguardless of what is going on.  My question is:

1.  What kind of affect does this have on my filesystem (ext3)?  Am I at serious risk of messing data up and loosing data in my /home directory?

2.  How does this affect the filesystem itself (the base installation)?  Can this 'break' my installation and cause me to have to re-install?  

Thanks.

Shane

---

### Post by Ocxic on 2007-12-26
I've had multipule power offs like that wihtout any negative affects, but you will eventually run into problems as that is not a very good way to power down. I would suggest looking into a UPS backup system, this will atleast allows you to shutdown properly.

---

### Post by shane2peru on 2007-12-26
> **Ocxic said:**
> I've had multipule power offs like that wihtout any negative affects, but you will eventually run into problems as that is not a very good way to power down. I would suggest looking into a UPS backup system, this will atleast allows you to shutdown properly.

Thanks for that suggestion, I have looked into that, however they are quite expensive here, and very difficult to get too.  I may have to do something like that.

Shane

---

### Post by tgalati4 on 2007-12-26
Look for used, metal case, APC-brand uninterruptible power supplies.  Businesses tend to throw them out because they don't know how to change the batteries.

Find a battery supplier in your area and put in new batteries.  You want one labeled "Smart UPS" or "Back UPS Pro" probably 400 or 600 VoltAmps (VA) rated.

There is a serial port in the back of these units.  With a special cable (that you can buy or make--search the internet) your UPS can shutdown your machine after a preset period of time when you lose power.  You need to load apcupsd and set up a configuration file, but it's not difficult.

You will get email messages that look like:

To: root@tubuntu2
Subject: tubuntu2 Power Failure !!!
Status: RO

Subject: tubuntu2 Power Failure !!!

tubuntu2 Power Failure !!!

APC      : 001,021,0585
DATE     : Tue May 22 22:39:43 PDT 2007
HOSTNAME : tubuntu2
RELEASE  : 3.12.4
VERSION  : 3.12.4 (19 August 2006) debian
UPSNAME  : TerryLab
CABLE    : Custom Cable Simple
MODEL    : DUMB UPS Driver
UPSMODE  : Net Master
STARTTIME: Tue May 22 22:39:41 PDT 2007
SHARE    : NetworkUPS
STATUS   : ONBATT SLAVEDOWN
MBATTCHG : 5 Percent
MINTIMEL : 5 Minutes
MAXTIME  : 30 Seconds
NUMXFERS : 2
XONBATT  : Tue Dec 25 04:23:06 PST 2007
TONBATT  : 20 seconds
CUMONBATT: 21 seconds
XOFFBATT : Mon Aug 13 14:30:29 PDT 2007
STATFLAG : 0x07060810 Status Flag
END APC  : Tue Dec 25 04:23:26 PST 2007

I had a windy Christmas Morning and the power went out, but luckily, the machine was shut down as expected.  But I lost 216 days of uptime!

You will get a log file that looks like this:

Wed May 09 17:24:06 PDT 2007  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Wed May 09 17:24:07 PDT 2007  Connect to slave hpubuntu failed. ERR=No route to host
Tue May 22 22:35:42 PDT 2007  apcupsd exiting, signal 15
Tue May 22 22:35:42 PDT 2007  apcupsd shutdown succeeded
Tue May 22 22:39:41 PDT 2007  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Tue May 22 22:39:41 PDT 2007  Connect to slave hpubuntu failed. ERR=Connection refused
Mon Aug 13 14:30:28 PDT 2007  Power failure.
Mon Aug 13 14:30:29 PDT 2007  Power is back. UPS running on mains.
Tue Dec 25 04:23:06 PST 2007  Power failure.
Tue Dec 25 04:23:26 PST 2007  Running on UPS batteries.
Tue Dec 25 04:23:57 PST 2007  Reached run time limit on batteries.
Tue Dec 25 04:23:57 PST 2007  Initiating system shutdown!
Tue Dec 25 04:23:57 PST 2007  User logins prohibited
Tue Dec 25 04:24:24 PST 2007  apcupsd exiting, signal 15
Tue Dec 25 04:24:24 PST 2007  apcupsd shutdown succeeded
Wed Dec 26 10:50:59 PST 2007  apcupsd 3.12.4 (19 August 2006) debian startup succeeded

---

### Post by shane2peru on 2007-12-26
Well, as I stated we live in Peru, South America, so getting these things is not an easy chore.  And there isn't any businesses around here throwing them away, I can assure you of that!  You can't buy them in the town I live in, in the capital city I may be able to buy one, but here, they don't throw anything away, they use all of it.  Everything here gets fixed and used.

Shane

---

### Post by tgalati4 on 2007-12-27
I've got 6 used APC's that I've collected over the past year.  If shipping wasn't so expensive, I would send you two!

Edit:  There must be Ubuntu users in Peru who know where to get a used UPS and get it to Shane.  He's too valuable a member to lose to a power outage!

---

### Post by dcstar on 2007-12-27
> **shane2peru said:**
> Ok, let me explain, I live in Peru where the power is not stable.  I have a stabalizer to help regulate the amount of power to  a stable output, however sometimes the flow of electricity dips so low that the stabalizer can't keep it's stable flow and everything shuts off and comes back on.  As a result using my desktop computer it gets shutoff about once every 2 weeks as if someone just pulled the plug reguardless of what is going on.  My question is:

1.  What kind of affect does this have on my filesystem (ext3)?  Am I at serious risk of messing data up and loosing data in my /home directory?

2.  How does this affect the filesystem itself (the base installation)?  Can this 'break' my installation and cause me to have to re-install?  

Thanks.

Shane

You can reduce any chances of data loss or corruption by turning off Write Caching on you disk drives (which will slow down disk performance but make it more reliable).

If you have IDE drives then the hdparm command/setup will do this, for SATA I'm not sure how it is done - it also may be in your BIOS settings.

A separate /home partition will also make your system more secure as any writes to that area will be in a different filesystem to your system/temp files.

---

### Post by shane2peru on 2007-12-28
> **dcstar said:**
> You can reduce any chances of data loss or corruption by turning off Write Caching on you disk drives (which will slow down disk performance but make it more reliable).

If you have IDE drives then the hdparm command/setup will do this, for SATA I'm not sure how it is done - it also may be in your BIOS settings.

A separate /home partition will also make your system more secure as any writes to that area will be in a different filesystem to your system/temp files.


Actually I do have a SATA drive, and my /home is on a separate partition.  Thanks for the tips.  I will google the 'Write Caching' on SATA drives to figure it out.  Thanks.

Shane

---

