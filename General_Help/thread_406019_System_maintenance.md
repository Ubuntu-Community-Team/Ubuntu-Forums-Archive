---
title: "System maintenance"
date: 2007-04-10
forum: General Help
---

### Post by Dragon43 on 2007-04-10
About once a month my "Ubuntu" does some sort of forced maintenance and it seems like maybe a defraging of some sort...?????

What is it doing and how would I do it say on a weekly basis?

What sort of system cleaning or what ever should I do on my stand alone "Ubuntu" machine?

I really want to keep my system lean and tight but I could not find anything in the FAQ's or by doing a search.

Any help would be appreciated.

---

### Post by srt4play on 2007-04-10
What you're seeing is fsck checking your filesystem(s) for errors.  This happens every 30 (I think) reboots.  I usually turn it off especially on my laptop because it annoys me.  If you want to change the number of times until the check happens, use this:

```
sudo tune2fs -c # /dev/xxxx
```

where # is equal to the number of startups that happen until the check and xxxx is equal to the partition you want to change, whether it be /dev/sda1 or whatever.

---

### Post by Dragon43 on 2007-04-11
Thanks for the info, I don't mind it, I was just wondering if there was somethings needed doing that I did not know about.  I do regulare back-ups and maintenance s
tuff on all the computers in the house and I just did not want to be letting something slide that I should be doing.

---

### Post by mssever on 2007-04-11
The system routine maintenance tasks that are scheduled by default are fsck, as mentioned earlier, and the stuff in /etc/cron* (don't edit /etc/crontab directly; use ```
crontab -e
``` for your crontab or ```
sudo crontab -eu root
``` for root's).

Unless you have a special setup, all the necessary routine maintenance is taken care of by default. /tmp is even cleaned every time you reboot, so it doesn't get bloated.

---

