---
title: "Wont boot - PLEASE HELP!!!"
date: 2007-09-14
forum: General Help
---

### Post by Markmiran on 2007-09-14
Hey  -  I have run into a massive problem with my ubuntu setup.  I was playing around with services and I noticed that both the kdm and gdm where tick for startup, so I turned on of them off in hope to use other.  As a result, I am now unable to boot into ubuntu at all.  I can still use recovery mode and run gdm that way, but to run it normally, it will boot to the point where gdm would normally start and bring up the splash screen, but it just freezes there.

Can someone please help me resolve this, have been reading posts for days - can't find anything, and I really don't want to have to reinstall everything again just for this.

Regards
Marky.

---

### Post by reckless2k2 on 2007-09-14
well if you "turned it off", why is it you can't turn it back on in recovery mode? If you turn it back on in recovery mode then you can boot normal and be fine. 

what are you running? kubuntu? ubuntu?

just turn them both back on and you'll be fine. hahaha. did you turn them off like this?

sudo chmod -x /etc/init.d/gdm
sudo chmod -x /etc/init.d/kdm


if so....just do this:

sudo chmod +x /etc/init.d/gdm
sudo chmod +x /etc/init.d/kdm


mark it as SOLVED. i'm earning cup icons here buddy!

---

### Post by Markmiran on 2007-09-15
Thanks for the post ... Wish it was that simple.  I have already attempted this with the gui and from the prompt - no luck.  When I boot it with normal mode, it just hangs , it seems to load something, but eventually hangs.  If I run it from recovery, and then load gdm - will work.  Must functions even work, except wont ready one of my disks.  Pain in the rear end, have no clues, and I am not that advanced enough yet to go diggen, not sure where to look.

Thanks again.
Marky

---

### Post by reckless2k2 on 2007-09-15
sounds like an x server issue. did you install proprietary drivers recently or fiddle with X at all like adding desktop effects?

---

### Post by Markmiran on 2007-09-15
No haven't touched any of it. All I did before this happened was open services, and unmarked the ticks, and this happened.  I think I might have to bite the bullet and reinstall everything.  Arrrggghh!!  Just when I had everything running almost perfect.  Anyway.

---

### Post by reckless2k2 on 2007-09-16
sounds strange considering. back your home directory prior to reinstall and you'll save a lot of hassle on reinstall.

---

