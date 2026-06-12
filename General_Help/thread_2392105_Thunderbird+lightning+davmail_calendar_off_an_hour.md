---
title: "Thunderbird+lightning+davmail calendar off an hour"
date: 2018-05-16
forum: General Help
---

### Post by jcwjcw42 on 2018-05-16
I've got an interesting problem that appears unique under Ubuntu (release 18.04). I'm running a DavMail server to access an Exchange account and accessing the calendar through the davmail caldav port from Thunderbird/Lightning. When I save an appointment through davmail it appears on the exchange calendar an hour later than set. (That is, if I set it at 8 AM it appears at 9 AM.) This happens both on a desktop and a laptop system running Ubuntu 18.04. Cases that work correctly:

Evolution on Ubuntu 18.04 writing to the davmail server.
Windows 10 on a different system writing to the davmail server.
Thunderbird+lightning running under Debian Stretch on the laptop using the same user home directory so identical Thunderbird profile.

I also tried running davmail as a user on the Ubuntu systems rather than using the server and got the same behavior. (Davmail as a user on Debian worked correctly.)

I checked and have the same time zone configuration under Ubuntu and Debian, but I still wonder if it could somehow be related to daylight savings time.

---

### Post by walts48 on 2018-05-17
The same time zone under Ubuntu and Debian.

What about Thunderbird? Preferences > Advanced > General tab Date and Time Formatting.

---

### Post by jcwjcw42 on 2018-05-18
> **walts48 said:**
> The same time zone under Ubuntu and Debian.

What about Thunderbird? Preferences > Advanced > General tab Date and Time Formatting.

The same, and in fact on the laptop I used the same Thunderbird profile under both Ubuntu and Debian (same /home directory mounted under both). That's what convinced me something is unique to Ubuntu.

---

