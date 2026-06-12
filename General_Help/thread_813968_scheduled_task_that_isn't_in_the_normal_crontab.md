---
title: "scheduled task that isn't in the normal crontab"
date: 2008-05-31
forum: General Help
---

### Post by Nathan_M on 2008-05-31
Hi,
When Hardy was still in pre-release, I became an update addict, and set up a cron to do apt-get update && sudo apt-get upgrade -y -d. For some reason... I can't remember why... I didn't do this using the normal crontab. I did it by adding a similar syntax to a very different file. Now I can't find it, and I'd like to change the automatic updates. I've tried searching the forums for the post that led me to this file, and I can't find it!

---

### Post by ezramorris on 2008-05-31
> **Nathan_M said:**
> Hi,
When Hardy was still in pre-release, I became an update addict, and set up a cron to do apt-get update && sudo apt-get upgrade -y -d. For some reason... I can't remember why... I didn't do this using the normal crontab. I did it by adding a similar syntax to a very different file. Now I can't find it, and I'd like to change the automatic updates. I've tried searching the forums for the post that led me to this file, and I can't find it!

It will take a long time, but if the worst comes to the worst you could always do:
```
grep -r "sudo apt-get upgrade -y -d" /
```

---

### Post by HalPomeranz on 2008-05-31
> **Nathan_M said:**
> Hi,
When Hardy was still in pre-release, I became an update addict, and set up a cron to do apt-get update && sudo apt-get upgrade -y -d. For some reason... I can't remember why... I didn't do this using the normal crontab. I did it by adding a similar syntax to a very different file. Now I can't find it, and I'd like to change the automatic updates. I've tried searching the forums for the post that led me to this file, and I can't find it!

You probably did it with anacron (run "man anacron" for a refresher).  That means your script probably ended up somewhere in /etc/cron.daily.

---

