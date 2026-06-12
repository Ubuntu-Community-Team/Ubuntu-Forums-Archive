---
title: "Bizarre speed problem"
date: 2007-05-03
forum: General Help
---

### Post by Complete Idiot on 2007-05-03
Let's see... I have an Acer laptop, with an Athlon XP-M 2400+ processor and 512MB RAM.
Anyway, before I upgraded to Feisty everything was fine but now it seems that whenever I boot up the computer without the Ethernet cable plugged in, the performance of the computer sinks and I get ridiculous things such as up to 1 minute to open my home folder or gedit.
At first I thought it could be a power management problem, but then I realised most of the time I was having this problem I had the laptop plugged, so I don't really understand what's happening...

---

### Post by rax_m on 2007-05-04
I think I read somewhere on one of the forums about some DHCP issues (??) on feisty.. might be worth checking out as your problem seems to occur when your network cable is out.

---

### Post by Complete Idiot on 2007-05-05
Hm, that kind of makes sense, as I have my Ethernet connection set to a static IP...

---

### Post by DagMan on 2007-05-05
Mine wasn't having that issue, and taking a quick look, I have wired networking enabled but if I click in the properties it is not set up, it's empty.
Roaming mode is unchecked and it's set for dhcp but other than that it's blank.  I'd suggest though, not worrying about any of that and trying out disabling it in general until you use it.  Hopefully that will work and it will also keep your settings for the next time you tick the little box next to 'wired connection'.

---

### Post by Complete Idiot on 2007-05-05
> **DagMan said:**
> Mine wasn't having that issue, and taking a quick look, I have wired networking enabled but if I click in the properties it is not set up, it's empty.
Roaming mode is unchecked and it's set for dhcp but other than that it's blank.  I'd suggest though, not worrying about any of that and trying out disabling it in general until you use it.  Hopefully that will work and it will also keep your settings for the next time you tick the little box next to 'wired connection'.


Oh, thanks a lot! It seems disabling the connection when I'm not using it fixes the problem. Thanks!

---

