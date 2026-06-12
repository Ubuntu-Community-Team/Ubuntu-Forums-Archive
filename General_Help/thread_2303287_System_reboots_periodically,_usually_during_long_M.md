---
title: "System reboots periodically, usually during long MATLAB simulations"
date: 2015-11-17
forum: General Help
---

### Post by sulimon510 on 2015-11-17
I often run code overnight, and every so often, usually during long simulations, the computer freezes for about 10 seconds and then reboots. I have paid attention to CPU temperatures using "sensors," and the computer always remains around 40C because of liquid cooling. I have changed the graphics card to a new one and that still doesn't solve the problem. It doesn't happen every-time I run overnight code, maybe one out of three nights, but it does seem random. I have checked /var/log/syslog, but it looks to me like all this text occurs after the reboot: 

 Nov 17 07:40:31 s anacron[3757]: Job `cron.daily' terminated
Nov 17 07:40:31 s anacron[3757]: Normal exit (1 job run)
Nov 17 07:41:00 s systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Nov 17 07:41:00 s systemd[1]: Started Bumblebee C Daemon.
Nov 17 07:41:00 s systemd[1]: Starting Bumblebee C Daemon...
Nov 17 07:41:00 s bumblebeed[4164]: [37356.722895] [ERROR]No integrated video card found, quitting.
Nov 17 07:41:00 s systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Nov 17 07:41:00 s systemd[1]: Unit bumblebeed.service entered failed state.
Nov 17 07:41:00 s systemd[1]: bumblebeed.service failed.
Nov 17 07:42:01 s systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Nov 17 07:42:01 s systemd[1]: Started Bumblebee C Daemon.
Nov 17 07:42:01 s systemd[1]: Starting Bumblebee C Daemon...
Nov 17 07:42:01 s bumblebeed[4167]: [37416.972773] [ERROR]No integrated video card found, quitting.
Nov 17 07:42:01 s systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Nov 17 07:42:01 s systemd[1]: Unit bumblebeed.service entered failed state.
Nov 17 07:42:01 s systemd[1]: bumblebeed.service failed.
Nov 17 07:43:01 s systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Nov 17 07:43:01 s systemd[1]: Started Bumblebee C Daemon.
Nov 17 07:43:01 s systemd[1]: Starting Bumblebee C Daemon...

Can anyone help me with where to start on troubleshooting this? Thank you so much for your time!

---

### Post by ian-weisser on 2015-11-18
Those log entries don't look like a reboot. They look like ordinary system activity...perhaps several hours after your failure.
Try the previous syslog for more useful messages - one of the things cron.daily does is to rotate the logs.

Do you have an NVIDIA Optimus requiring bumblebee? If so, it seems misconfigured. If not, you should uninstall bumblebee.
But that may be unrelated to your problem.

The proper (previous) syslog should contain clues on what kind of crash you are suffering.
If it's a real reboot (uptime resets to 0.000), then you likely have a thermal failure (hardware).

However, since your log show an uptime of about 10 hours (37416.972773 seconds), you might just have an X crash. When X crashes, it kills your session, loses your data, and returns you to a login prompt. Not a reboot at all...but hard to tell the difference if you're not sitting there watching it occur. The proper logs will easily show the difference. X can crash for many reasons - corruption, out-of-memory, bumblebee conflict, display problem, etc.

First step is to determine if you have a real reboot or an X crash using the previous day's syslog.

---

### Post by Topsiho on 2015-11-18
Looks like a hardware problem to me.

As it occurs during long (Matlab) calculations some hardware is protesting, which it doesn't during normal work.
You changed your graphics card. Has the new one sufficient specifications? New doesn't always mean that it is OK, might be broken too.
You said your CPU remains at 40C according to sensors, so that (if you trust sensors) is out.
Then you have your hard disk: is that OK? You might check the S.M.A.R.T. information using the disk utility (or how that is called in English). 
Check it's temperature too while doing heavy duty work.
How is your RAM memory? You might do a memory check. Maybe during heavy duty work a part of it is used, that is not used in normal work.
How clean is the interior of your computer case? And computer parts? Just a little blow with compressed air might do miracles...

These are only ideas, I am not an expert, but that's what I would check first.

Topsiho

---

### Post by sulimon510 on 2015-11-18
Ok thanks, I will try all of those things.

---

