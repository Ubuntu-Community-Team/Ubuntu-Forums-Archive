---
title: "How to stop syncing system time in 16.04?"
date: 2017-03-28
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-03-28
For various reasons, I need my system time to be incorrect.  In Lubuntu 14.04, I could achieve this just by purging all the ntp-related packages, and then setting the time how I want.

I've now upgraded to Xubuntu 16.04, and I can't figure out what's syncing the time.

[FONT=Courier New]dpkg-query -W | grep -i ntp[/FONT] does not output anything.  And I have disabled the systemd time sync -
```
$ timedatectl status
      Local time: xxxxxxxxxxxxxxxxxxx
  Universal time: Tue 2017-03-28 15:51:05 UTC
        RTC time: Tue 2017-03-28 15:51:05
       Time zone: xxxxxxxxxxxxxxxxxxxxxxxxxx
 Network time on: no
NTP synchronized: no
 RTC in local TZ: no

```

What is syncing the time, and how do I disable or uninstall it?

---

### Post by texpat on 2017-03-28
sorry, I just read you tried timedatectl..

---

### Post by SeijiSensei on 2017-03-28
Maybe it's the hardware clock.  Try this:
```

sudo date --set='1-jan-2017 00:00:00 GMT'
sudo hwclock --systohc

```
That sets the date to midnight GMT on January 1, 2017, then sets the hardware clock to the same time.

---

### Post by &amp;KyT$0P# on 2017-03-28
Thanks SeijiSensei, that looks promising. :D

I've just tried that, shut down & powered off my computer, and rebooted, and the time is still where I want it to be.  If it stays there for the next couple days, I'll mark this solved.

---

