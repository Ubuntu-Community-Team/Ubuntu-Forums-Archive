---
title: "Gutsy reboots every hour!"
date: 2008-01-05
forum: General Help
---

### Post by dgermann on 2008-01-05
Hi--

At 13 minutes past the hour, every hour, my gutsy box reboots.

This morning, we had a power outage, a couple of them within about an hour of each other. According to syslog, the first of these caused a reboot at 8:13 am. Logs on my server from the smart-ups on that box show "line voltage notch or spike" at  9:28, 8:07, and 8:06 am.

This rebooting started at 1:13 pm, after I had been working on it since about 10:20 am.

Here is my crontab--I see nothing there that would cause this strange behavior.
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

####copied from sdb1 (old drive) and refers there 20071208: did not work so commented out for now; changed to new locations 20071210:

0 * * * * root /usr/sbin/esets_update

##############ddg 20061113 updated for new directories 20071210:

0 3 * * * root /usr/sbin/esets_scan -l --mail –unsafe / -- -/dev* -/proc* -/sam* -/media/sdb1/dev* -/media/sdb1/proc* -/media/sdb1/sam*

##############

30 * * * *      root    cp -pru ~doug/.evolution /sam/vol22/comm/evo/




```
This machine is used in a production environment, so this is something I need to fix quickly.

Any ideas how to trouble shoot this, please?

Thanks!

---

### Post by dgermann on 2008-01-06
Hi all--

A followup, in case it helps someone else. Can't say it is solved, as you will see.

There has been more strangeness, perhaps it is good.

After posting here, I shut down this box, unplugged the power and the ethernet as well as the mouse and keyboard, replugged all, restarted, and there have been no more involuntary reboots.

I did check the server and there were no other power spikes or problems reported. The whole building has a surge arrestor on the power system and it is still functioning.

Strangeness # 2. Another computer on my network lost power during this power spike and then we were unable to boot it. It stopped at or just after the Intel bootup screen (prior to grub) and reported an "error 106." We unplugged all, took it to the tech people, and they could not repeat the problem--it booted right up for them. (Of course!) So we brought it back here and it worked fine for us too. That's what gave me the idea to unplug this system.

So strangeness on strangeness.

Does this tell us there is a problem that needs looking at more? Or just let it go for now, now that all seems OK?

---

### Post by ~LoKe on 2008-01-06
Sounds like a PSU and/or hard drive is on its way out.

---

### Post by dgermann on 2008-01-06
~LoKe--

Yup, I spose. Or if I am lucky it was just a need to clear out some registers or nvram.

Thanks!

---

### Post by Bruce S on 2008-01-07
dgermann ,

     As your computer is used in a production environment , I strongly advise you to invest in a UPS ,
 to protect yourself from all those nasty spikes, brown outs surges and blackouts.
     I have had one for about 5 years and it has saved me on quite a few occasions.
    
     Only exception has been a force 6.8 earthquake we had here just before Christmas.
     That does not happen very often!

---

### Post by dgermann on 2008-01-10
Bruce and ~LoKe--

I want you each to know that I am very thankful for your help.

It has now be about 5 days and it has not shut down once during that time. And the other computer has been running flawlessly, too.

Yes, and the spike protection is important. It is probably belt and suspenders seeing that the whole system has that protection on it, but I may be a belt and suspenders kind of guy....

Thank you each, very much! Have some popcorn on me! :popcorn:

---

### Post by tomgriffing on 2008-03-11
I'm experiencing this hourly reboot behavior, too.
New Gateway Quad core desktop w/Nvidia Graphics.
I disabled cron and anacron and most other daemons.
I booted to Knoppix and ran something to stress test the machine - it ran for days without rebooting.

Then, when running Ubuntu 7.10, 64 bit, I hear the fan go to high speed, then the system reboots.

From /var/log/messages:

Mar 11 01:55:09 phoenix dhcdbd: Started up.
Mar 11 02:15:06 phoenix -- MARK --
Mar 11 02:35:07 phoenix -- MARK --
Mar 11 02:55:21 phoenix syslogd 1.4.1#21ubuntu3: restart.
Mar 11 02:55:21 phoenix kernel: Inspecting /boot/System.map-2.6.22-14-generic

Mar 11 02:55:24 phoenix dhcdbd: Started up.
Mar 11 03:15:21 phoenix -- MARK --
Mar 11 03:35:22 phoenix -- MARK --
Mar 11 03:55:40 phoenix syslogd 1.4.1#21ubuntu3: restart.
Mar 11 03:55:40 phoenix kernel: Inspecting /boot/System.map-2.6.22-14-generic

Mar 11 03:55:43 phoenix dhcdbd: Started up.
Mar 11 04:15:40 phoenix -- MARK --
Mar 11 04:35:40 phoenix -- MARK --
Mar 11 04:55:58 phoenix syslogd 1.4.1#21ubuntu3: restart.
Mar 11 04:55:58 phoenix kernel: Inspecting /boot/System.map-2.6.22-14-generic

Mar 11 04:56:01 phoenix dhcdbd: Started up.
Mar 11 05:15:58 phoenix -- MARK --
Mar 11 05:35:59 phoenix -- MARK --
Mar 11 05:56:14 phoenix syslogd 1.4.1#21ubuntu3: restart.
Mar 11 05:56:14 phoenix kernel: Inspecting /boot/System.map-2.6.22-14-generic


Any help would be greatly appreciated.

Tom Griffing

---

### Post by dgermann on 2008-03-11
Tom--

No cure-all solution, but have you tried unplugging all the wires, waiting a bit and then reconnecting and starting over?

That and knowing the secret mantra to say over the machine (man secretmantra) while unplugged, is what worked for me. ;)

---

