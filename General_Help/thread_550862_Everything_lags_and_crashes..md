---
title: "Everything lags and crashes."
date: 2007-09-14
forum: General Help
---

### Post by IamAcoconut on 2007-09-14
Here's the problem, that arose last week (that hadn't happened before to neither this nor any other Ubuntu installation on my PC):

Everything's fine when the gnome boots, but after running more than two applications, i.e. firefox, pidgin, thunderbird and liferea, at least one will occasionally lag, and eventually **hang** itself (which I resolve using xkill) or the **entire system** (then I have to use the power switch)

It **doesn't matter what programs** I run, OR in what order. I do use compiz-fusion, but switching back to metacity gives me nothing - Strangely Compiz' effects work pretty smoothly even when other things lag, and it gives me the advantage of knowing, when something bad happens to an app - the window which stops responding immediately goes black&white.

Just about prior to noticing this problem, I installed and uninstalled two games: America's Army for linux and Vegastrike. Both installation and deletion was conducted via scripts, apt-get not involved. I have also compiled mixminion just before recently, but this installation seemed successful.

Help greatly appreciated - my Ubuntu install is very polished and is running on an encrypted drive, so I would really like to avoid reainstalling. Thanks in advance!

---

### Post by kuja on 2007-09-14
I ran into a mess of problems when running ubuntu on an encrypted drive. Could be worthwhile to check your /var/log/syslog file for any possible errors.

---

### Post by IamAcoconut on 2007-09-15
I noticed thttpd in syslog and under ps -axf which I had installed recently and now removed it. That seemed to help a bit, but the issue remains.

What should I look for in my syslog, or my processes?
What info should I provide you with to give an insight of the situation?

---

### Post by IamAcoconut on 2007-09-17
How do I check whether my SWAP is ok? System monitor currently tells me that 70% out of 512MB of my RAM is being used, and swap is not being used at all yet.

---

### Post by kuja on 2007-09-17
That's interesting, I'm not sure how one would check that ... I guess one way of checking would be to disable and/or delete the swap, and perhaps create a swapfile and use it for a while to see if it is behaving. Also, how can you be sure it's not being used at all yet? Or if you're worried about it, perhaps just disabling would be enough. Anyhow, another interesting thing to check might be the individual application logs if you weren't seeing any *really* interesting ones in the syslog (I reckoned there might be some if everything is crashing like crazy) Hmmm, what else, ah yes, have you ran memtest yet? If not do so ...

---

### Post by IamAcoconut on 2007-09-21
> how can you be sure it's not being used at all yet?
->> System monitor

> Anyhow, another interesting thing to check might be the individual application logsHow?

> if you weren't seeing any *really* interesting ones in the syslog (I reckoned there might be some if everything is crashing like crazyFirst of all, most of the syslog means nothing to me - I don't know what to look for, what is suspicious, and what's ordinary. Secondly when more then one app crashes, the entire system crashes, and after reboot the syslog is gone.

> have you ran memtest yet?I did - nine times, 'cos I hadn't been entirely sure what to do to it ;-) No errors.

---

### Post by kuja on 2007-09-25
When I say individual application logs, that's assuming that they have any also. Keeping in mind that *most* logs are stored in /var/log. 

It really is a pity that you're losing the syslog, that might be killing the chance to track down what's wrong. If you're not sure about the syslog, post what you have, who knows, could be something useful still ... maybe. 

Do you run into these stability issues when running from a livecd?

---

### Post by IamAcoconut on 2007-09-27
> **kuja said:**
> When I say individual application logs, that's assuming that they have any also. Keeping in mind that *most* logs are stored in /var/log. 
None of the (major) apps I use are there. Except for Tor (yet it's a daemon), which did cause some problems, yet there's nothing suspicious in the logs. 

> **kuja said:**
> Do you run into these stability issues when running from a livecd?
Haven't checked after things started to go bad (everything fine before). I will in a moment. Although...

Here's the part of my syslog - starting just before the time when everything started crashing.
```
Sep 27 17:32:50 jack-laptop -- MARK --
Sep 27 17:52:55 jack-laptop -- MARK --
Sep 27 18:12:55 jack-laptop -- MARK --
Sep 27 18:17:03 jack-laptop /USR/SBIN/CRON[11080]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 27 18:25:03 jack-laptop kernel: [10479.996000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Sep 27 18:25:03 jack-laptop kernel: [10479.996000] ata2.00: (BMDMA stat 0x25)
Sep 27 18:25:03 jack-laptop kernel: [10479.996000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
Sep 27 18:25:03 jack-laptop kernel: [10479.996000]          res 51/24:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
Sep 27 18:25:04 jack-laptop kernel: [10479.996000] ata2: soft resetting port
Sep 27 18:25:04 jack-laptop kernel: [10480.644000] ata2.00: configured for UDMA/33
Sep 27 18:25:04 jack-laptop kernel: [10480.644000] ata2: EH complete
```

Can this be an explanation? Dunno what to do yet :/

---

### Post by IamAcoconut on 2007-10-06
A desperate little *bump*

---

