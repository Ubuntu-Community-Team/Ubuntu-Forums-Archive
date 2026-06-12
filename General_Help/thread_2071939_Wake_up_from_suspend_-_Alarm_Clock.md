---
title: "Wake up from suspend - Alarm Clock"
date: 2012-10-16
forum: General Help
---

### Post by MongoDB on 2012-10-16
Hello guys, I completely switched to Ubuntu a few months ago. I want to wake up with the computer from suspend. In windows I used scheduled tasks and tick a option to wake the computer for this task. In Ubuntu I set a cron job, but I don't how to make the computer to wake up from suspend. Is it possible?

I use Ubuntu 12.04 LTS, and my MB is H67MA-UD2H-B3, if it's something connected with the BIOS.

---

### Post by Toz on 2012-10-16
**rtcwake** will do that for you. Have a look at this thread for a couple of examples: [http://ubuntuforums.org/showthread.php?t=1822517]("http://ubuntuforums.org/showthread.php?t=1822517") (posts #5 and #9).

More info on rtcwake can be found here: [http://manpages.ubuntu.com/manpages/precise/man8/rtcwake.8.html]("http://manpages.ubuntu.com/manpages/precise/man8/rtcwake.8.html")

---

