---
title: "reset the system???  12.04"
date: 2012-12-09
forum: General Help
---

### Post by shelac on 2012-12-09
I have been using UBUNTU 12.04 with Apache2 as a developmental server for several weeks.  This afternoon I experienced a power interruption on the machine and now I am unable to connect to it through Filezilla or a browser.
   
  I tried re-booting the machine, doing a restart on Apache2 as well as a restart on vsftpd with no success.
   
  Until now I was thinking that the thing was quite bullet proof.  I would regularly shut the thing down by just using the power button on the CPU and pressing it again when needed to get it up and running and it behaved flawlessly.  I guess that the power interruption must have happened at exactly an in-opportune time.
   
  Before I reinstall everything I was wondering if anyone had any ideas that I might try to salvage the situation.  Is there a method to perform a complete reset of everything that might solve my dilemma?

---

### Post by rnerwein on 2012-12-10
> **shelac said:**
> I have been using UBUNTU 12.04 with Apache2 as a developmental server for several weeks.  This afternoon I experienced a power interruption on the machine and now I am unable to connect to it through Filezilla or a browser.
   
  I tried re-booting the machine, doing a restart on Apache2 as well as a restart on vsftpd with no success.
   
  Until now I was thinking that the thing was quite bullet proof.  I would regularly shut the thing down by just using the power button on the CPU and pressing it again when needed to get it up and running and it behaved flawlessly.  I guess that the power interruption must have happened at exactly an in-opportune time.
   
  Before I reinstall everything I was wondering if anyone had any ideas that I might try to salvage the situation.  Is there a method to perform a complete reset of everything that might solve my dilemma?
hi
oh you shutdown and reboot a unix/linux box by using the power button only.

i wish you much fun in future :-)     :-)

---

### Post by arpanaut on 2012-12-10
If you have physical access to the system boot up a live cd/dvd/usb and run the disk utility and do a file system check on each partition.  

Learn the proper way to shutdown and restart your system and you will have a healthier system and avoid HDD errors.
If you can afford it get a UPS battery backup and this will avoid power outage issues.

HTH

---

### Post by shelac on 2012-12-28
It seems as though a re-install of the system is the answer for me.  And this time when I get it working I will create a image of the O/S in case it happens again.

---

### Post by Beatsleigher on 2012-12-28
Well, you should listen to what the others said.

I mean, I may be kind of new to Ubuntu, but not to computers in general.
Shutting down a computer (Including Servers, laptops, Towers, SFFs, and/or some consoles), you will just break something, something as delicate as computer hardware cannot be treated like that.

Learn to shut down a computer, before moaning about things like that.

---

### Post by Mopar1973Man on 2012-12-28
Ok for newbies I tend to suggest Webmin for a console for server stuff and system stuff... But I would check the system logs for errors or maybe the service just isn't fired up.

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by shelac on 2012-12-30
Well, there is some actual advice from Mopar1973Man.  Thank you!  Much more appreciated than a bunch of lectures.  Being mighty green to this I haven’t a clue what you mean by “the service just isn't fired up” but I will try to do a bit of research to learn what I can.
   
  This Ubuntu installation is on an old CPU that was destined for the recycle bin anyway and if it died I wouldn’t shed a tear.  It is very slow as well but as a dev web server it works just fine.  For anything else it would end up in the scrap bin in a flash.  Rather than reverting back to WAMP I thought that it might be interesting and educational to mess around with Ubuntu to come up with a developmental server.  For me at least, one of the cardinal rules of computing is that you need to experiment a great deal to find out what works and just as importantly, what doesn’t, and it is best to do this in an environment where it costs nothing in terms of dollars or lost data.  This fills the bill nicely.
   
  It is interesting to note that in all of the years that I have been using computers, I have encountered a great deal of instances where there have been power interruptions and there has never been a time when the Windows (or DOS in the old days) machine failed to recover and the only loss might have been a document that I was working on at the time.  I live in a rural area where it is not uncommon to experience a few glitches in the electricity delivery system and at the office there were the occasional situations where someone flipped a breaker or kicked a power cord.   I always thought that LINUX was rock solid and wouldn’t let a little thing like a temporary power loss cause it any grief.
   
  And as for Beatsleigher’s interpretation of my request for some suggestions as “moaning”, he/she should aim to contribute something helpful.  Check the dictionary for a definition of “moan” and try again. And try not to make it personal please. The sarcasm from the others doesn’t help the dialog either.

---

