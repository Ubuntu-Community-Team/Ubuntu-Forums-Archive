---
title: "cron file changed on it's own"
date: 2020-03-14
forum: General Help
---

### Post by Rick Churchill on 2020-03-14
I had several backup script setup in the admin cron file and just released that they have not been running for several days. When using sudo crontab -e, I get the following:  

0 0 */3 * * /tmp/.X19-unix/.rsync/a/upd>/dev/null 2>&1
5 8 * * 0 /tmp/.X19-unix/.rsync/b/sync>/dev/null 2>&1
@reboot /tmp/.X19-unix/.rsync/b/sync>/dev/null 2>&1
0 0 */3 * * /tmp/.X19-unix/.rsync/c/aptitude>/dev/null 2>&1

This is nothing like what the original cron was when I set it up.  My user cron file is showing similar changes even though I had never set it up to do anything.  I can't think of any changes I've made other then some modifications to my netplan settings.  I had to buy a new router and reset the address on my server so it stays static.

OS is Ubuntu 18.04 server and am curious what would have caused cron to change on it's own.

---

### Post by TheFu on 2020-03-14
Just a guess, but I would guess the system has been hacked.  
You'll need to figure out how they hacked in and close those wholes ASAP.  What services does the system run?
**Comment out all the crontab lines, ASAP.**

There's no reason any cron task from /tmp/ anywhere would be used.

I would backup those files somewhere to share with us and disconnect from the internet.

---

### Post by HermanAB on 2020-03-15
Well, rsync is a backup tool, so it looks like you played with a backup utility and it modified crontab for you.

---

