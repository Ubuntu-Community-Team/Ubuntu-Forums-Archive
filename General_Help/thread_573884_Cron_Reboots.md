---
title: "Cron Reboots?"
date: 2007-10-12
forum: General Help
---

### Post by iljmez on 2007-10-12
I'm having a weird problem, my pc reboots every day 30 minutes past  midnight.
Could be related: Taking a look at the var/log/messages there is an entry from  syslogd: Oct 12 07:38:25 mypc syslogd 1.4.1#20ubuntu4: restart. This is in the logs every day, around the same time.
I've taken a look at /etc/cron.daily scripts and there is no reboot in any of them, nor anything looks out of the ordinary in the logs. 
Any ideas as to why the pc could be reboting?

---

### Post by devilears on 2007-10-12
can you open a terminal/console and type: at -l <enter>

---

### Post by mbeierl on 2007-10-12
Might also be something in your BIOS that tells the machine to shut down at a specific time.

---

### Post by iljmez on 2007-10-13
at -l didnt return anything...

I doubt it's the bios since this did not happen with any other linux distribution i had installed previously...

So it's not cron... Any other ideas?

---

### Post by wub on 2007-10-14
I currently have this problem on my laptop (originally 6.10, recently upgraded to 7.04 - no change), and I hoped there would be help here.  But I have a desktop that I have installed other distros on (currently also 7.04) and it used to do this with MythDora, - one of the reasons I switched it to Ubuntu.  The desktop no longer does this.

I have looked in crontab, and at the configuration files for at and anacron, but I don't see anything that seems to be scheduled for that time ( 4 minutes after midnight).

I noticed right from the install that my battery ran down overnight after I 'shut down' my system, so I have been taking the battery out, but it was only recently that I found out what was really happening.  I am tired of kludging around this.

As far as some kind of BIOS interaction, the laptop came with XP, and I have set it up to dual boot.  It shuts down properly from XP.  I can't understand what processes would still be running after a 'real' halt.

I am going to try using ctrl-alt-2 (pick a number lower than 7) to get to a non-X console, sudo, and run 'shutdown -P -H now' to see if this helps.  The -H option says 'Halt the system after bringing it down' and -P says 'Power off the system after bringing it down' according to the man page.  Both seem redundant to the whole idea of shutdown, to me.

More later.

---

### Post by wub on 2007-10-15
Oh, well.

I tried shutting down from a 'real' console, using sudo to run 'shutdown -HP now', hoping that by specifying that I really wanted to power off the system, that all processes would stop.  Nope.  This time, instead of booting at 00:04, it booted at 00:08 - if that helps to diagnose the situation.

Hmmm,  well the first two messages are:

Oct 15 00:08:52 ook syslogd 1.4.1#20ubuntu4: restart.
Oct 15 00:08:52 ook anacron[5201]: Job `cron.daily' terminated

So, even though I tried to explain clearly that I wanted my system halted (wouldn't that kill every process?) and powered down (wouldn't we need to restore power to get anything to run?) it just poped back up.  I guess all these months, when I forget and shutdown from Ubuntu and don't remove the battery, it must be booting to the login prompt, even though the lid is shut (isn't that another signal - to hibernate?) and waits for me to log in, until the battery goes flat...

I suppose I could try manually killing off everything that is not essential for a shutdown before calling shutdown.  I can't see how that would help.  From the first day I installed Ubuntu, even before I started adding new applications, this has been happening.  I can't figure out where the configuration mistake might be.

---

