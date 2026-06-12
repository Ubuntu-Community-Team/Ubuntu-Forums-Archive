---
title: "Backup server - how do I save some power?"
date: 2007-06-21
forum: General Help
---

### Post by namityadav on 2007-06-21
I have recently installed dapper with backuppc on an old machine. I plan to use it as a backup server for our two laptops (Wife's Windows XP and my Fiesty). The backup is working fine (At least for my laptop ;) ), but I am concerned about the power that the machine is going to eat up. 

Is there any way I can set up the machine to go on a power-saving mode within 2 mins of inactivity, but wake up every time backuppc scripts have to start up to check for any live laptops to backup? Or if I can set up the machine to sleep all day, and wake up only during those few evening hours when we usually have the laptops on?

---

### Post by CrispyFried on 2007-06-21
in some PCs you can configure the PC to turn itself on at a particular time via the BIOS. you might then be able to tell it to turn itself off via script or power management after the backups are done.

---

### Post by namityadav on 2007-06-21
Thanks for the reply. I don't think my decades old BIOS would have that feature :) In any case, how would it automatically switch on then? Perhaps what I need is a "Wake-on-time" kind of a feature that is initiated by the OS residing in the memory .. so that the disk / fans etc can sleep during other hours

---

### Post by shizeon on 2007-06-21
Not sure if your network card supports WOL (wake on lan) or not, but I use it for a similar purpose.  Basically this allows you to send a magic-packet to the server which will wake it up on demand.  The repos have a linux util that can do this called etherwake.   I'm sure there is something similar in the windows world that you could script in on your wife's pc.   

Depending on your network card you might be able to also enable a general wake on any traffic option, which would fire up the pc anytime a packet is directed at it.  

I guess the main problem I see is that the connections would have to initiated from your computers.  So this may not be an option with your current setup.

There is a howto here on how to enable on your system: 
[http://ubuntuforums.org/showthread.php?t=234588&highlight=WOL]("http://ubuntuforums.org/showthread.php?t=234588&highlight=WOL")

Hope this helps.

---

### Post by CrispyFried on 2007-06-21
how old is the PC? does it have a "soft" power switch or the old style "on-off" switch that stays locked on once pressed? if it is you might just leave the power switch in the "on" position and try an external timer like those used to control lights - tell it to turn on at 5 PM say. but that still leaves the problem of how to turn it off gracefully as you certainly dont want it to just turn off without a proper shutdown. maybe you could shut down via script and the OS will shut down (but not power off) and wait till the external timer shuts it off.

what kind of PC is it?

not sure how much power you would save just by turning off the fans and drives.

I was thinking of doing something similar to what you have but I plan on using an old notebook with an external usb or firewire drive. that way I figure the whole thing will draw under 50 watts or so and I wouldnt mind that being on 24/7.

---

### Post by namityadav on 2007-06-21
shizeon,

The motherboard supports WoL, but the ethernet card doesn't. Considering that such cards sell for less than 10 bucks, I am seriously inclining towards that option. I found a few programs for it on wikipedia: [http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN). As for initiating the connection, this is okay (At least on my laptop) - I can have a cron script on the laptop trying to send the message to the backup-server every hour. This will fail when I'm not at home, and will work when I am.

CrispyFried,

Yeah, an old notebook is an ideal candidate for things like these. Less noise, low power and less space - perfect

---

