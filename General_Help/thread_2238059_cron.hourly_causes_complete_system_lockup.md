---
title: "cron.hourly causes complete system lockup"
date: 2014-08-05
forum: General Help
---

### Post by crowley.kyle.r on 2014-08-05
Hi there,

I've been fustrated over the past few days with these random crashes, but it seems like this one might be the root cause of the problem. 

Basically, my system has been locking up a seemingly random times. The entire system would just crash. Mouse would move, but everything else was completely locked up. Just completed crashed.

In the past, the crash would happen every few hours (maybe 3). I decided to jump into /var/log/syslog and dig around for some evidence. I found that there was a kernel panic that was likely due to a segmentation fault in Chrome (I have since reported the bug). I stopped using Chrome and moved over to Chromium. That seemed to fix the issue, because there were no crashes.

Now we are here...

About 30 minutes ago (15:17 EST) the system locked up again, exactly like it did in the past. I figured it might be Chromium acting up as well (since Chrome is based on Chromium) but I did not find anything is syslog related to Chromium.

Here is a snippet of syslog:

```

Aug  5 15:09:01 optiplex780 CRON[2928]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug  5 15:17:01 optiplex780 CRON[3182]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly

```

Those were the last two lines in syslog before the crash. Everything is okay at 15:09 but as soon as we get to 15:17, the entire machine locks up. 

So, I decided to dig into /etc/cron.hourly to see what was there that may have been screwing things up. Come to find out, that directory is EMPTY (aside from a hidden file called .placeholder).

So, I have no idea why this is causing the crash. Is CRON trying to run commands that aren't there. I am really confused as to why this is happening.

Please leave any suggestions. Don't feel afraid to ask for more info if it will aid in your assistance.

---

### Post by ian-weisser on 2014-08-05
From your description, cron seems innocent.
Cron was the last process to *successfully* run and leave a log entry. 

Something later, that did not leave a log entry, crashed.

---

### Post by crowley.kyle.r on 2014-08-06
Is there any way that I can figure out what might be causing it. I haven't had a crash today (fingers crossed) so I'm hoping it was a fluke.

---

### Post by ian-weisser on 2014-08-06
Any entries in /var/crash ?
Does your system ever pester you to send error reports?

---

