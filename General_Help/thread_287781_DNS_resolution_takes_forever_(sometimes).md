---
title: "DNS resolution takes forever (sometimes)"
date: 2006-10-29
forum: General Help
---

### Post by compwiz18 on 2006-10-29
When I try to resolve domains in any program except Firefox, it takes about 20/30 seconds to resolve.  This is annoying...  What I can tell you that might be useful: I'm using ndiswrapper with a cursed Broadcom 4318.  If I use the native drivers with my Broadcom 4318, this doesn't happen.  However, I'm using the 64bit version of Edgy now for max processor power, and the native drivers don't work in 64bit, so I'm stuck with ndiswrapper.  This only happens at my house, doesn't happen at school.  I suspect this has to do with IPv6 not being supported by my WRT54g Linksys router, but I can't prove that...the reason I think this is the problem is because if I leave IPv6 support in Firefox on, it takes forever to resolve domains too... Without it, its ultra quick.  If I turn IPv6 support on at school, it's just as fast as with it off.

To summarize: I want to know how I can stop Edgy from using IPv6, if this is possible.

Thanks in advance.

---

### Post by wieman01 on 2006-10-29
"ipv6" seems to be your problem indeed: [http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

---

### Post by compwiz18 on 2006-10-29
Bingo!  That wasn't it, but adding ipv6 to the module blacklist did it :D

btw, the module blacklist is at **/etc/modprobe.d/blacklist**

I just added ipv6 to the end of it.

Thanks for your help :D

---

### Post by wieman01 on 2006-10-29
Hi, yeah, same thing actually.

Strange thing happened with the link above. Have replaced it & now it seems to work. But it linked to the wrong website, my apologies. Now idea how that could happen. 

Glad you got it working.

---

