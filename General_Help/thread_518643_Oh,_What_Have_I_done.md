---
title: "Oh, What Have I done?"
date: 2007-08-06
forum: General Help
---

### Post by Thanatos10 on 2007-08-06
I've been trying to figure out how I screwed up my system, but so far no luck on my own.  So I turn to the Ubuntu Guru's for some help.

If I try and start Ubuntu, Feisty Fawn x64, normally it will seem to start, but I have no video.  I can hear it get as far as mounting the CD-ROM, then nothing.  However, if I select the recovery mode option at boot-up, press CTRL-D when prompted and do nothing after I'm asked to enter my user id the system will start normally after 3 or 4 seconds.  I originally thought I'd screwed up the GDM so I reloaded that and no help.  Checked my video drivers (nvidia Linux-x86_64 ver 100.14.11) but everything seems normal (well as normal as nvidia drivers get).

Does the system generate a "start-up file" so I can see where the system stops responding when booting normally?  That would be a help, it would at least give me a place to start looking.

Thanks for any thoughts anyone might have on this.

Scott.

---

### Post by nitro_n2o on 2007-08-06
have  a look at /var/log/syslog /var/log/bootstrap.log /var/log/boot everything is there in /var 
maybe your hardware isn't compatible with 64bit ubuntu.. maybe you need the 32

---

### Post by Thanatos10 on 2007-08-06
Thanks, I'll check them out.  I've been using the 64-bit version for a few months now and this just started happening last weekend.  No new programs or hardware as far as I can remember.  That's not say the kids didn't have their way.

Scott

---

