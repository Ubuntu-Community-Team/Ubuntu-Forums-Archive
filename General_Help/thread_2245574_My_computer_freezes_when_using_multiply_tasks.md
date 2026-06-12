---
title: "My computer freezes when using multiply tasks"
date: 2014-09-24
forum: General Help
---

### Post by ftp2 on 2014-09-24
Yo

7 days ago i decided to clean up inside my machine , I was dedicated to be very careful while cleaning, to not fck up something.
I was cleaning whit something like this:
[IMG]http://bit.ly/1msYEvT[/IMG]

It's soft and flexible.

**Anyways**, after that event, my computer starts to randomly **freeze** after a while using multiply tasks such as browsing web and listening to music.  (nothing special)

It happens few times a day.

I did ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` but it doesn't fix anything. I have to restart my computer to start working.

Help?

---

### Post by ian-weisser on 2014-09-25
Yo

Call back your soft and flexible whatever-it-is (maybe you meant to put a link there?) and undo whatever you did.
Or perhaps tell us what you actually did. Step by step, in order.

---

### Post by ftp2 on 2014-09-25
**I did nothing.** Beside hardware cleaning my computer.

I switched to Ubuntu 2 months ago, first month I had no problem using it, but after a month my computer starts randomly freeze without reason. Once its frozen, the only solution is reboot.

On side note: I used to update and upgrade system once per week. I have no additional software beside the one that comes whit Ubuntu installation.

Thanks for reply, hopefully we will find solution for this problem. :cool:

---

### Post by ftp2 on 2014-09-25
[size=7]bump![/size]

---

### Post by gifford on 2014-09-25
Maybe more information about you computer would be helpful. In particular, the amount of ram, video card, cpu, etc.

---

### Post by ian-weisser on 2014-09-25
Are there any .crash files in /var/crash?
Any useful errors in /var/log/syslog?
Is there _anything_ you can reliably do to make the crash occur?

Could also be a hardware fault - intermittent, unpredictable, and changed behavior caused by physical disturbance (cleaning).

---

### Post by ftp2 on 2014-10-26
Yo ian-weisser, there are no any crash files in /var/crash dic. However there are **** loads of **same** reports in /var/log/syslog
example one of many would be
```
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.653813] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) went below the 'critical' thresholdOct 26 13:27:38 Kazuya-GanG kernel: [ 1348.658016] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) hit the 'critical' threshold
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.813074] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) went below the 'critical' threshold
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.841349] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) hit the 'critical' threshold
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.845557] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) went below the 'critical' threshold
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.853922] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) hit the 'critical' threshold
Oct 26 13:27:38 Kazuya-GanG kernel: [ 1348.858126] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) went below the 'critical' threshold
Oct 26 13:27:41 Kazuya-GanG kernel: [ 1352.052795] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) hit the 'critical' threshold
Oct 26 13:27:41 Kazuya-GanG kernel: [ 1352.470873] nouveau  [  PTHERM][0000:02:00.0] temperature (105 C) went below the 'critical' threshold

```


Every second.

---

### Post by ftp2 on 2014-10-26
I had 3 crashes in 1 hour, just fcking black screen and nothing. I have to click restart button. any idea what is this ****?

---

### Post by ian-weisser on 2014-10-26
Well, those "temperature (105 C) hit the 'critical' threshold" log entries sure looks like overheating.
The lack of .crash files suggest overheating, too. Hardware faults are a common form of failure that leave no .crash files (because it's not a software crash).

Perhaps the temperature sensor is faulty, or perhaps your prior cleaning changed the airflow, or perhaps the fan(s) are not working...or unplugged.

---

### Post by ftp2 on 2014-10-26
I set the psychical fan to chill the computer, since then no crashes. but this is temp solution, any idea what should i do with my cooler inside to fix this shhit ?

---

### Post by ftp2 on 2014-10-26
Btw i set up psensor to monitor my CPU temperature and fan speed

---

### Post by Thee on 2014-10-27
Is the CPU fan spinning? Is it mounted correctly?

---

