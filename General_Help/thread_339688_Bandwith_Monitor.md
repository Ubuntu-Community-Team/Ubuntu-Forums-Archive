---
title: "Bandwith Monitor"
date: 2007-01-16
forum: General Help
---

### Post by RavenndudE on 2007-01-16
I'm looking for a tool that will run in the background and set it so that is my downloads + uploads for the day reach a certain limit, it kills a program (or runs a script that kills a program).

Here at school there is a 1gig bandwidth limit per day thet resets at midnight. So I'm looking for something that will kill my torrent program (ktorrent) when I get to like 990mb or something (Have to give some room for the laptop too =)  )

Thanks

---

### Post by kidders on 2007-01-16
Hi there,

If you feel brave, you could write yourself a cron script that would execute a few "killall"s based on the output of ifconfig eth0|grep "RX bytes".

---

### Post by amo-ej1 on 2007-01-16
negative, the rx/tx counters of ifconfig wrap. if you were to use that you'd be using that wrapped delta's over a given interval of time.

---

### Post by kidders on 2007-01-16
> **amo-ej1 said:**
> negative, the rx/tx counters of ifconfig wrap. if you were to use that you'd be using that wrapped delta's over a given interval of time.Yep... to use that particular counter, you'd have to be a bit clever about it.

---

### Post by amo-ej1 on 2007-01-16
wouldn't it be easier to have you torrent client limited to a certain bandwidth  (900 * 1024) / (24*60*60)  byte/sec and keep it running 24/7 ?

---

### Post by RavenndudE on 2007-01-16
> **amo-ej1 said:**
> wouldn't it be easier to have you torrent client limited to a certain bandwidth  (900 * 1024) / (24*60*60)  byte/sec and keep it running 24/7 ?

It may be, but that doesn't count or my normal downloading and internet usage.

---

### Post by kidders on 2007-01-16
I can certainly see the attraction of an application-independent monitor. Rolling your own (with cron & a shell script) is relatively straightforward, although such a script would often need to run as root, which would have security implications.

As amo-ej1 pointed out, the only wrinkle would be getting a reliable count of bytes in/out. Using iptables or the ifconfig tool are two options, but you would have to watch out for occasions when the counters might reset themselves.

I once did something like what you're describing on my own box, purely for information purposes, by caching byte counts in a /tmp file. The only change I would suggest to your plan is to build in some advanced notice of an approaching download limit. "sudo killall ...." is a sort of an extreme thing to suddenly execute out of the blue. A notice that says something like "Warning: All your internet-related apps will be killed in another 30MB." would be less cruel!

---

