---
title: "Windows 10's Clock is affected by the Dual boot"
date: 2018-10-30
forum: General Help
---

### Post by drpeppercan on 2018-10-30
Hi all,


I found [this tutorial]("http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/") on how to fix this by either changing how the time is handled by either Ubuntu or Windows 10.
The problem is, it says that Ubuntu maintains the Real Time Clock in Universal Time (UTC). However, when I go to Linux Mint (19) and check what RTC it is using (timedatectl) it tells me:
```
$ timedatectl
                      Local time: Tue 2018-10-30 09:39:53 EDT
                  Universal time: Tue 2018-10-30 13:39:53 UTC
                        RTC time: Tue 2018-10-30 13:39:53
                       Time zone: America/Toronto (EDT, -0400)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

```
The time I see showing in the taskbar (lower right corner) is correct at 09:39am (EDT). This is the opposite of what the tutorial is saying.
This tutorial is over 2 years old now. 
[B]Can anyone say with certainty that this tutorial applies today, or not?
If not, what is the new procedure?
[/B]


Thanks in advance guys!

---

### Post by nlee2 on 2018-10-30
I just use ntp

---

### Post by dbergst on 2018-10-30
I have used the tutorial referenced by the OP and it works correctly here.

---

### Post by Impavidus on 2018-10-31
By default, Ubuntu keeps the RTC on UTC. However, when the installer detects that Windows is present, Ubuntu is automatically configured to keep the RTC on local time. Which may occasionally give problems when switching between summer time and standard time (as happened in Europe last Sunday and will happen in North America next Sunday). You only have to configure this manually if the installer didn't detect Windows, if you install Windows after Ubuntu or when you remove Windows. It was already like that the first time I installed Ubuntu, 12 years ago. The tutorial is correct, but doesn't mention this detail..

So in your case, everything on the Linux side is as expected. In what way is Ubuntu affecting the Windows clock?

---

### Post by missmoondog on 2018-10-31
this isn't any help, but i had this same error on one of my laptops that at the time was running windows 7 and lubuntu 16.04. forget exactly how far off it made the clock in windows off by, but seems like it was an hour or 2. i used that same tutorial but it didn't fix my issue either. never did figure it out. just thought i'd mention this to let you know you're not the only one who has seen this problem here.

kind of a lie. i did fix the issue by wiping windows off the computer!! :)

---

