---
title: "hdparm spindown values above 240 do not work."
date: 2020-03-18
forum: General Help
---

### Post by killwarez on 2020-03-18
Hi all, I am running 18.04 LTS Server version of Ubuntu as a Plex server. I am trying to get the HDDs to spin down after 1 hour of idle time. I set my parameters in /etc/hdparm.conf

Standby values 1-240 go in 5 second increments. So setting it to 240 makes the drive spin down in 20 minutes.  When I set this, it works without any issues.

Values 241 through 251 go in 30 min increments. Id like to set it to 242, which should be 1 hour. But it doesnt work, drives never spin down. I also tried 241 (30 min), drives never spin down.

How can I troubleshoot this? And/or maybe use something alternative to hdparm?

---

### Post by HermanAB on 2020-03-19
$ man hdparm

-S: "Note that some older drives may have very different interpretations of these values."

In other words: YMMV

---

### Post by killwarez on 2020-03-19
> **HermanAB said:**
> $ man hdparm

-S: "Note that some older drives may have very different interpretations of these values."

In other words: YMMV

Thanks for the input, the drive was manufactured less than a year ago. Its a 6TB WD Purple.

---

