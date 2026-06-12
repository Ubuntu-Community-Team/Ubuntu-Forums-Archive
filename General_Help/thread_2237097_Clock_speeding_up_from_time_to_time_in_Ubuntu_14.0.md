---
title: "Clock speeding up from time to time in Ubuntu 14.04"
date: 2014-07-30
forum: General Help
---

### Post by RobotMa on 2014-07-30
Hi,

I just installed Ubuntu 14.04 64-bit on my DELL XPS 15z, and I chose the acpi=off to get it through. Now, everything works just fine except for one thing: my clock (time and date) is speeding up from time to time, the clock of the system can pass 10s in one second. And I think my mouse and keyboard also suffer from this unsynchronization, where my cursor will speed up flashing to the extreme and then come back to normal and same thing with the keyboard when I'm ttyppppppppppppppppppppppppppppppppping, just like now.

Could someone tell me how to fix this? It seems not uncommon for Linux to have this time synchronization issue but it happens one time per minute and is a real pain in the ass.

Thanks

---

### Post by TheFu on 2014-07-30
Install **ntp** and configure it to sync time from an internet time server.  This will keep the machine at sub-second accuracy forever. BTW, NTP solved this issue like ... er ... 30 yrs ago.

My local NTP server has these lines inside the /etc/ntp.conf:
```
server pool.ntp.org
server ntp.ubuntu.com

```
Of course, there are many other lines ... those two are the most important.

The thing that is odd to me is that I don't have any issues with Linux time keeping, but forever (since 1993) have problems with MS drifting massively to the point that I've forced all my MS systems to synchronize every 15 minutes - hourly wasn't enough to prevent 5+ minute errors.  The issue has happened with every MS OS I've used in that time.  At one job, I had access to MS Engineers and they claimed that +/- 5 minutes was close enough for any desktop. I was appalled. Accurate time is central to crypto and security.

---

### Post by RobotMa on 2014-08-01
Hi, thanks for your reply first.

I included the code you wrote but it doesn't solve the problem. I blogged a little bit and it seems that ntp can only solve a relatively slow time drift, around 1s per minute. My computer is drifting 20s per minute and do you know how to solve that?

---

### Post by TheFu on 2014-08-01
20s / min?   Time to buy a new motherboard.  Normally, wrong clocks are cause by dead CMOS batteries, but that only happens if the machine is powered off.  Could the wrong timezone be set for the system?

If the drift is happening while powered on and it isn't related to batteries, TZ, disconnected from the internet - I'd think it was a HW issue, IMHO.

---

