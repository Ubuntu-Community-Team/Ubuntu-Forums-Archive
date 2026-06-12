---
title: "This setup worked perfectly"
date: 2007-05-24
forum: General Help
---

### Post by antiemptyv on 2007-05-24
In case anyone is thinking of building an Ubuntu system, here's my setup that worked perfectly for Feisty, first time around, no configuration (except for turning changing the wireless setting from "roaming" to "manual configuration").

**CPU**: AMD Athlon 64 4000 SanDiego Core Socket 939 CPU 
**Motherboard**: Mach Speed MSNV-939 Socket 939
**Video Card**: EVGA GeForce 7600 GT
**Wireless Adapter**: Linksys WMP54GS PCI Wireless Network Adapter - 54Mbps, 802.11g

Compiz and Beryl worked perfectly (though I've reverted back to Compiz for its apparent better stability).  No issues for about two weeks now.  I was wary of having to do some configuration, but I didn't need to do any.  Very excited.

---

### Post by angryfirelord on 2007-05-24
Glad to see that your system is running well.

Usually the issue that Linux has is hardware that is really new, not yet understood well enough to write a driver,  or only works with proprietary software (with the exception of a few).

---

### Post by antiemptyv on 2007-05-24
Yeah.  My other computer (Compaq Presario 2100 Laptop from about 2003) had isses all the time, so it's nice to have one run so smoothly--and be so flashy!

---

### Post by braddcadd on 2007-05-31
Did your WMP54GS work without NDISwrapper?  Other posts claim they need WINE or ndis to get this to work.

---

### Post by antiemptyv on 2007-06-13
actually, yes!  it worked for a while, but then the system began to freeze up on  me.  so i had to blacklist the rt61 driver and use ndiswrapper to install the rt2500 driver.  here is what was going on with the rt61 driver: [http://ubuntuforums.org/showthread.php?t=471867](http://ubuntuforums.org/showthread.php?t=471867)

---

### Post by antiemptyv on 2007-06-17
ok.  so, i don't know what's going on now.  system froze up on me again, requiring me to reboot.  on bootup, froze at the same spot.  so, as i did last time, i blacklisted the rt61 driver.  then even after installing the rt2500 driver via ndiswrapper (like last time, which *worked*), the wireless adapter wasn't able to be configured--not showing up in any configuration program, i.e. network-admin. 

so, i *un*blacklisted the rt61 driver, and things are working fine.  soooo now i think i may never reboot again.  

any ideas?  i'm thinking a new wireless card may be in order, but who knows if that's the real problem.  i've never experienced anything like this before.  is this thing ever going to act right?

---

### Post by antiemptyv on 2007-06-27
so, my system froze up on me a couple more times, so i've just installed 32-bit ubuntu on my amd64.  i read the rt61 driver behaves in the 32-bit flavor.  so far so good.  fingers are crossed.

---

### Post by antiemptyv on 2007-12-31
I was just going through old threads I began to mark them as [SOLVED] if they were in fact solved, and I figured I'd just add an update in case anyone wants to use any similar hardware.  It's about six months later and all is going well.  ..very well indeed.  I just installed Gutsy recently--no freezes or major issues at all.  Even managed to get help on here to get the wireless adapter working.  Very pleased.

---

