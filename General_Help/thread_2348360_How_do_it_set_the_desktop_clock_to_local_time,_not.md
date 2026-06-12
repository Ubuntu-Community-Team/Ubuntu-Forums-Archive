---
title: "How do it set the desktop clock to local time, not UTC?"
date: 2017-01-03
forum: General Help
---

### Post by steve169 on 2017-01-03
I'm running Ubuntu 16.04.1.

The desktop clock at the upper right corner shows the correct local time, but when I exit Ubuntu and boot Windows 7, the Windows clock has been changed to Greenwich time (UTC).

How can I correct this?

---

### Post by Olav on 2017-01-03
I believe this is the command that you are looking for:
```
sudo timedatectl set-local-rtc true
```
The command creates a configuration file /etc/adjtime with this content:
```
0.0 0 0
0
LOCAL
```
The "LOCAL" keyword in there means the computer internal clock (RTC) is always going to be set to local time.

Use the "timedatectl set-local-rtc" command with a parameter of "false" after you deleted Windows. It will delete /etc/adjtime and restore sanity...

Now it *should* also be possible to arm-twist Windows into using a UTC RTC and still show local time in the graphical interface. I believe it is some sort of registry key that you need to edit. Perhaps Google can help you with that.

---

### Post by Impavidus on 2017-01-03
> **Olav said:**
> I believe this is the command that you are looking for:
```
sudo timedatectl set-local-rtc true
```
Correct, or according to [this post]("https://ubuntuforums.org/showthread.php?t=2321876") you can use 1 instead of true.

It's better to use UTC than local time for the RTC as that doesn't cause confusion when changing time zone or daylight saving time, but most important is using the same time on both systems.

Even better would be to keep the RTC on the monotonically increasing [TAI]("https://en.wikipedia.org/wiki/International_Atomic_Time"), from which UTC is derived by subtracting a fixed offset and leap seconds, but that's another point.

---

### Post by steve169 on 2017-01-03
Many thanks to you. We newbies would be lost without you guys.

---

