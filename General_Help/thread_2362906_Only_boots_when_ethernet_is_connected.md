---
title: "Only boots when ethernet is connected?"
date: 2017-06-03
forum: General Help
---

### Post by fidelio2 on 2017-06-03
Hi all,
So I had a go at setting up a super light installation to run on an old eee pc. I installed the base Ubuntu 17.04 and then installed:
xorg, wicd, openbox, lxdm, chromium-browser 

That's basically all I want, literally a netbook. Everything works fine when connected to ethernet. I can even unplug the ethernet cable once it has booted and wireless works perfectly. 

But it won't boot unless the ethernet is connected. What on earth could be the cause?
Super thanks,
F
Edit: It did boot eventually. It just took about 5 minutes. So why would that be?

---

### Post by Autodave on 2017-06-03
Check your BIOS and make sure that it is not booting to LAN: that would be my first check.

Just noticed that you installed Ubuntu: that will slow that poor machine down tremendously. I would got for Xubuntu or Lubuntu: much much lighter distros: same packages available.

I just buried an EEEPC last week: it ran Xubuntu with no problems.

---

### Post by fidelio2 on 2017-06-03
Thanks. Will check bios. But as to the second point, I only installed the base system from a mini Iso, then added openbox, wicd etc. The base system in all the 'buntus is the same, right? Or is there a difference in the base install between versions. I had to install xorg manually, so it's not like the Ubuntu iso is bundled with loads of bloat.

---

### Post by Autodave on 2017-06-03
I misread/misunderstood that part....sorry. I would definitely check the BIOS then.

As I said before I had an ASUS EEEPC: 1 gig RAM, 700 mhz processor and it ran Xubuntu just fine: took a little over a minute to boot to a workable desktop. If all else fails, you may want to give that a try.

---

