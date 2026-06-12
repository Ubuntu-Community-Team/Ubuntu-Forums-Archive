---
title: "Cron alarm clock help"
date: 2008-03-20
forum: General Help
---

### Post by hypnoctopus on 2008-03-20
Hello there - I've been struggling with trying to get my crontab to act as an alarm clock to no avail.  Can anyone help me figure out what I'm doing wrong?

here's the line in my crontab:

```
30 10  *   *   *     /home/apollonios/meds

```

Which executes this script:
```
#!/bin/sh
vlc -vvv /home/apollonios/meds.mp3
```

Now, the script works fine, it's executable and everything, but cron just DOES NOT execute it, no matter if it's in my crontab or the root crontab or what.

Please help?

---

### Post by Oldsoldier2003 on 2008-03-20
> **hypnoctopus said:**
> Hello there - I've been struggling with trying to get my crontab to act as an alarm clock to no avail.  Can anyone help me figure out what I'm doing wrong?

here's the line in my crontab:

```
30 10  *   *   *     /home/apollonios/meds

```

Which executes this script:
```
#!/bin/sh
vlc -vvv /home/apollonios/meds.mp3
```

Now, the script works fine, it's executable and everything, but cron just DOES NOT execute it, no matter if it's in my crontab or the root crontab or what.

Please help?

try:
```
30 10  *   *   * DISPLAY=:0 vlc -vvv /home/apollonios/meds.mp3
```
you may have to give the full path to VLC

---

### Post by hypnoctopus on 2008-03-20
Thank you so much!  that did it!  Yaaaay! :D :D :D :D

---

