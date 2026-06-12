---
title: "Is it time counting bug or hardware issue?"
date: 2020-05-11
forum: General Help
---

### Post by bijaydeyp on 2020-05-11
Hello members

My problems' details below...
   I have multibooted laptop with Windows & different ubuntu distros. If the BIOS clock is set as per local time 9:00 am of 10th May,2020 then Windows(offline) preconfigured with Indian time zone shows 9:00 am in morning. Ubuntu(offline) preconfigured with Indian time zone shows 2:30 pm of same day.  Kubuntu(offline) preconfigured with UK time zone shows 10:00 am of the same day.
 And it is vice-versa i.e if I sync any particular ubuntu distro with internet(online), the BIOS clock gets changed.
   My temporary workaround is unticking auto-sync option.  

I am searching for solutions. 

Best regards

---

### Post by CelticWarrior on 2020-05-11
[https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot#169384](https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot#169384)

---

### Post by Impavidus on 2020-05-11
It's not a bug; it's a weird design choice in Windows. Windows keeps the clock on local time, but every other system keeps it on UTC.

---

### Post by bijaydeyp on 2020-05-12
Many thanks @[URL="https://ubuntuforums.org/member.php?u=1826209"][B][COLOR=#000000]CelticWarrior
[/COLOR][/B][COLOR=#000000]Did not  know that. Very useful info[/COLOR]**[COLOR=#000000].[/COLOR]**[/URL]

---

### Post by bijaydeyp on 2020-05-12
Many thanks for the explanation @[URL="https://ubuntuforums.org/member.php?u=1417721"][B][COLOR=#000000]Impavidus
[/COLOR][/B][COLOR=#000000]I will just change the time zone to iceland / Greenland.[/COLOR][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

