---
title: "Ubuntu and Windows Can't Seem to Agree What Time It Is."
date: 2016-06-09
forum: General Help
---

### Post by DeadlyOats on 2016-06-09
Heck!  Kubuntu can't decide what time it is!

1) I checked the time set on my BIOS (UEFI), and it's set to the correct time and date.

2) When Kubuntu's log on screen comes up, it says one time (10:06 AM 9 June 2016 - that time is the wrong time).

3) When I'm logged on.  It shows the correct time (5:06 PM 9 June 2016 - the correct time).

4) When I log out of Kubuntu and log into Windows, Window's time is changed.  I have to reset it to the correct time each time I switch from Kubuntu to Windows.

How do I get all of these time differences to agree and Window's time to remain unchanged?

---

### Post by Bashing-om on 2016-06-09
DeadlyOats; Hey . hey ;

Windows sets the hardware clock to local time by default. Linux/Unix sets it to UTC by default. One of them needs changing so they both use the clock the same way. -> [http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)
To tell your Ubuntu system that the hardware clock is set to 'local' time:

edit /etc/default/rcS
add or change the following section # Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no
Always make a backup of any file that is to be edited. Never can tell what might perchance.

You need to have root privileges, which means using sudo.
 Windows defaults to considering the hardware clock to being local time. Ubuntu (and pretty much all *NIX systems) defaults to considering the hardware clock to be UTC. So every time you boot Windows it's "fixing" the hardware clock, and setting it back 8 hours from UTC to your local time.

[INDENT][INDENT]all in the effort of
[INDENT][INDENT][INDENT]co-operation[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2016-06-10
Yes, a timezone mix-up is the problem, but the solution has changed on 16.04: [http://ubuntuforums.org/showthread.php?t=2321876](http://ubuntuforums.org/showthread.php?t=2321876)

---

### Post by Bashing-om on 2016-06-10
@Impavidus; Ouch ! Thanks for that !

Had slipped my mind that systemd (16.04) might be a factor. Mind re-adjusted.

[INDENT][INDENT]the times
[INDENT][INDENT][INDENT]they are achange'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DeadlyOats on 2016-06-10
Thank you, both, for your replies!  Thank you, Impavidus, for your very easy to understand answer.  This very easily solved my issue.  Now, everyone on my computer (UEFI, Kubuntu, and Windows) agrees on the time!  (LOL)

---

