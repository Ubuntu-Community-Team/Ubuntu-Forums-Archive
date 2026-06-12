---
title: "Boot Problem"
date: 2007-06-19
forum: General Help
---

### Post by adamorjames on 2007-06-19
Well, I'm using Ubuntu 6.06 and when I try to boot my laptop to Ubuntu most of the time it gets stuck at reading files to boot or something similar to that. What happens is it goes from the nice Ubuntu boot screen with the logo to a black and gray screen with words similar to reading files to boot. It just stops there. Any solution?

---

### Post by phidia on 2007-06-19
From the boot menu you can try to boot in safe mode or you might try the install cd and the rescue a broken system option. If you've done any updates or upgrades recently you could also try booting an older kernel-provided that optiion is still available in your grub menu. Hope that helps.

---

### Post by adamorjames on 2007-06-19
I have a different kernel I can boot from but it's  386 and I have two processors so I'm guessing that wouldn't be ideal. What do you mean rescue a system option? Also, I don't have a safe mode option but I do have a recovery option which I've already tried and it said something about kernel panic.

---

### Post by psusi on 2007-06-19
Your problem description is too vague to get any help.  You need to be specific about exactly what is going wrong, and describe what you did to get it into this state.  The only answer I can give to a general "help, my system won't boot" beyond trying rescue mode is to reinstall.  Reinstalling might not be a bad idea either since 6.06 is now a year and two releases old.

---

### Post by phidia on 2007-06-19
> **adamorjames said:**
> I have a different kernel I can boot from but it's  386 and I have two processors so I'm guessing that wouldn't be ideal. What do you mean rescue a system option? Also, I don't have a safe mode option but I do have a recovery option which I've already tried and it said something about kernel panic.

If you can be more specific (what is the exact error?) that would be helpful. 
I don't know if it was available on 6.06 but later versions have had an option from the boot menu on the cd to rescue a broken system. 
Chances are if you're getting a kernel panic that an update or other system change was made that prevents correct booting. Knowing the specific error message should help people here to help you.

---

### Post by adamorjames on 2007-06-19
OK, Grub loads up.
Ubuntu logo appears.
Below the logo it shows what's happening -
```

Loading essential drivers... ok
Mounting root file system... ok
Reading files needed to boot... ok

```
It stops right at that last line and goes into a black screen with light gray text and reads-
```

*Reading files needed to boot... [ok]

```
That's as far as it goes.
I'm using a Toshiba laptop A105 S4284.
I have to take the battery out and try it again and hope that it gets past the "Reading files to boot..." line.
Also, I'm using the kernel 2.6.15-28-686 because I have two processors.

You probably want to know about the recovery kernel panic too.
When I try the recovery option it goes through a lot of things and then it stops and the last two lines say-
```

[17179573.489000]<0>Kernel panic - not syncing : Attempted to kill init!
[17179573.492000] _

```

---

### Post by adamorjames on 2007-06-19
So phidia you're saying that if I upgrade to a newer Ubuntu that I can do the recover system option? I think that may be the way to go then. How new does it have to be? 6.10? Also, psusi said that 6.06 is a year and two releases old so I'm guessing that means I should upgrade too.

---

### Post by phidia on 2007-06-19
I think edgy was a good release (just my opinion tho) and there's really nothing to keep you from trying feisty 7.04 Having said that the "Recover a broken system" option, from the live or install cd is not a blanket cure for everything. Your current system is probably fixable. I'm sure there are threads here on that error message I'm including a general explanation from linuxquestions [http://www.linuxquestions.org/questions/showthread.php?t=353920](http://www.linuxquestions.org/questions/showthread.php?t=353920)

---

### Post by adamorjames on 2007-06-20
I'm a bit leery of Fiesty at the moment. My wireless won't work in  the live CD. I might try Edgy though, when I get a chance. Thanks.

---

