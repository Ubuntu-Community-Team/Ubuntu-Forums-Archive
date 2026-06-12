---
title: "Digital Clock applet showing UTC instead of local time (but with the local time label"
date: 2013-05-12
forum: General Help
---

### Post by heehau on 2013-05-12
I noticed this today and I don't know whether it's something that came with 13.04 or newer.

I have the digital clock applet set to showing Local time (America/Los Angeles, Pacific, UTC-08). Instead, it will show UTC. What is really strange is that the applet knows and displays the correct time for all other time zones. I already had display set for a series of time zones, and they continue to display correctly. A different Pacific time zone, (America/Tijuana) will display the correct time. Only my local time is shifted to UTC.

At first I thought this is just me not knowing how to set time properly, but I noticed the display looked something like this:
[FONT=Fixedsys]Sunday, May 12 2013
Honolulu: 02:50 PM

Monday, May 13, 2013
Los Angeles: 12:50 AM

Sunday, May 12, 2013
Tijuana: 05:50 PM
New York: 08:50 PM

Monday, May 13, 2013
UTC: 12:50 AM
Rome: 02:50 AM[/FONT]

Obviously, I have a workaround (looking at the time in Tijuana instead of Los Angeles) but the bug seems rather egregious for an applet whose main function in life is to show me the correct time.

Does anyone have any ideas? Is it Kubuntu only, or is KDE in general affected? Is this new? Does anyone else see this?

---

### Post by heehau on 2013-05-14
Figured it out, and it's a problem that probably comes from the installation: /etc/localtime is set to a link to the correct time zone, but the link is broken.

It SHOULD be: /usr/share/zoneinfo/SystemV/PST8PDT -> /etc/localtime
It actually IS: ../SystemV/PST8PDT -> /etc/localtime

I guess with the broken link, it thinks localtime is UTC. As soon as I fixed the broken link, time was back to normal.

---

### Post by moebius50178 on 2013-05-23
This also fixes the problem:

```

sudo dpkg-reconfigure tzdata 
sudo ntpdate pool.ntp.org

```

The main problem is still there anyway because if you enter to date&time configuration, symlink is overriden and does broke again.

---

### Post by mcmlviii on 2013-06-28
> **heehau said:**
> Figured it out, and it's a problem that probably comes from the installation: /etc/localtime is set to a link to the correct time zone, but the link is broken.

It SHOULD be: /usr/share/zoneinfo/SystemV/PST8PDT -> /etc/localtime
It actually IS: ../SystemV/PST8PDT -> /etc/localtime

I guess with the broken link, it thinks localtime is UTC. As soon as I fixed the broken link, time was back to normal.

/usr/share/zoneinfo/Los Angeles is a relative symlink. KDE copies that file, but because it's a relative link, it doesn't work when copied to /etc.

But for me even correcting the symlink didn't work. I had to use moebuis's solution.

---

