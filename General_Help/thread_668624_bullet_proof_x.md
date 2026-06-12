---
title: "bullet proof x"
date: 2008-01-15
forum: General Help
---

### Post by travm on 2008-01-15
This is a real pain the butt.  I installed the restricted drivers for my tnt2 through the restricted driver manager, and it just doesnt work.  It tries 3 times to load X, then loads this failsafe crap, and i cant even read the logs to find out what happened because the logs just say, you are using failsafe mode, blah blah blah.  

This card "should" work, and it should get direct rendering.

Other people have gotten tnt2's to work with gutsy so why is it that mine feels the need to load failsafe all day.

nv driver works, but only after i make the change, then do a hard reboot.  soft reboots remain in failsafe mode.  

i am not a noob, but by no means an expert but this is drivering me crazy.

if anyone has any idea how I can disable this failsafe junk so i can properly trouble shoot, or anything else i can try that would be awesome.  
I dont have the bandwidth to download 10 different drivers and try them all.  but if thats the only way it will take me about 2 weeks.
thanks.

---

### Post by heindsight on 2008-01-15
You can disable the BulletProof-X failsafe mode by commenting out the line:
```
FailsafeXServer=/etc/gdm/failsafeXServer
```
in /etc/gdm/gdm.conf

---

### Post by travm on 2008-01-15
thx2u sir,
I will try that, 
hopefully my half angry rant didn't discourage anyone from helping me.
I expect around this time tommorow i will have logs that say stuff that i dont understand :)

Thanks again.

---

### Post by yabbadabbadont on 2008-01-15
I ran into the same issue with my Geforce4 TI 4200.  I ended up being so annoyed, that I wiped the drive and restored Gentoo from a backup.  :lol:

OK, now for an on-topic suggestion.  Make sure that the restricted driver manager installed the **legacy** version of the nvidia drivers.

---

### Post by travm on 2008-01-16
yeah it did, ive now downloaded envy, and the drivers from nvidia's website, and i'm gonna try doing the 12 driver thing tonight.  
any thoughts on how i check which version of the proprietary driver has been installed by ubuntu?  i saw a few bug fixes on the changelog for a september 2007 legacy driver on the nvidia website.  some of them sound promising for me.

---

