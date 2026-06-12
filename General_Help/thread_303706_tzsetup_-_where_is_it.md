---
title: "tzsetup - where is it?"
date: 2006-11-20
forum: General Help
---

### Post by Apostata on 2006-11-20
Howdy,

  I've got a strange situation where, even though my local timezone is set to EST (as it should), my system is still set to UTC which ends up stamped on all of my email (tangent: why it would bypass the user timezone is beyond me). Apparently, running 'tzsetup' can clear this up, but it's nowhere to be found on Edgy (Kubuntu) - can anyone clarify how to solve this?

Thanks.

---

### Post by mssever on 2006-11-20
I'm not a KDE user, but there should be a time app somewhere (probably available from System Settings). It sounds like perhaps your system clock is set to UTC and your e-mail client incorrectly gets its time from the system clock instead of system time.

Try setting your timezone to America/Toronto (Linux seems to be ignorant of timezone names, such as EST, CST, etc) and toggling the system clock uses UTC option (or whatever it's called).

---

### Post by Apostata on 2006-11-21
Unfortunately that didn't work - I went into KDE settings, switched the NTP server, double-checked the timezone. When I hit Apply - the clock changed back momentarily to the proper time (this is the clock in the KDE settings, not on the toolbar). However, when I sent an email to myself, the timestamp was +5 hours ahead (ie UTC).

It would be nice to have a operating system that told the correct time.:-?

---

### Post by mssever on 2006-11-21
> **Apostata said:**
> Unfortunately that didn't work - I went into KDE settings, switched the NTP server, double-checked the timezone. When I hit Apply - the clock changed back momentarily to the proper time (this is the clock in the KDE settings, not on the toolbar). However, when I sent an email to myself, the timestamp was +5 hours ahead (ie UTC).

It would be nice to have a operating system that told the correct time.:-?

Hmm... I've never encountered those difficulties. Does the clock in the panel display the correct time? What email client are you using? Is it only that program that is having problems?

---

### Post by Apostata on 2006-11-21
> **mssever said:**
> Hmm... I've never encountered those difficulties. Does the clock in the panel display the correct time? What email client are you using?

Clock in the panel works fine - that's what I find odd. As root I tweaked the KDE settings (complete with locale) and while it works fine for the panel (as user), obviously my email client (Kmail/Kontact) reads a different system setting. I've also checked /etc/timezone and it's set to Toronto (as it should)

> **mssever said:**
> Is it only that program that is having problems?

Unfortunately no - I just did a test (created a text file) and it's dated 5 hours ahead.

---

### Post by mssever on 2006-11-21
Is your hardware clock set to UTC or local time? The easiest way to find out is to check the clock in your BIOS (if it has one) or boot into a live CD/other OS. My theory is that it's set to UTC and the clock on your panel is making a timezone correction, while the rest of the system thinks that the hardware clock is set to local time. Traditionally, UNIX systems are set to UTC and adjust to display local time.

I haven't been able to figure out where that setting is made. I looked at KDE and didn't see anything (but then, I don't use KDE much). I couldn't find the setting in Gnome, either, though I could have sworn that it was an option in the date and time dialog. I also searched through /etc in vain. I must be missing something...

One further test you could do, assuming that the hardware clock is set to UTC, is to set it to local time in the BIOS. Then, the panel clock should be off--which is easy enough to fix--and everything else should be right. The question is, what will happen if you enable NTP (auto-updating the time from the Internet)? Besides, this is more of a workaround than a fix.

---

### Post by Apostata on 2006-11-28
Yeah, my BIOS shows the correct time - this is the odd thing. I'm totally in the dark as to what the problem could be. One thing I'm considering, even though it's going to be a *huge* PITA, is deleting my .kde folder.

My theory is that there may be conflicting settings in there, as I've upgraded/installed Ubuntu several times over the last couple of years and my /home is on a separate partition that I've never wiped-off. The problem is that it means spending a day setting-up defaults on a lot of KDE apps.

Bloody frustrating.

---

### Post by santo on 2006-11-28
mssever is probably right about the hardware clock being UTC instead of local (or vice versa)
In that case you need to modify the UTC parameter in /etc/default/rcS

(also take a look at [http://www.ubuntuforums.org/showthread.php?t=135214&page=2](http://www.ubuntuforums.org/showthread.php?t=135214&page=2))

---

### Post by Apostata on 2006-11-28
Here are the contents of /etc/default/rcS:

> TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no


Also I found 'tzsetup' (thanks), but it still seems to have no effect. I logged-out/logged-in and when I send an email to myself, it's timestamped 16:02 (UTC) instead of 11:02 (EST).

Strange.

---

### Post by santo on 2006-11-29
Well, we suspect your hardware clock being set to UTC.
In that case, you should say UTC=yes in your /etc/default/rcS file (instead of UTC=no)

---

