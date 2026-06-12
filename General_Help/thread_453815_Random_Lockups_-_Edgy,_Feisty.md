---
title: "Random Lockups - Edgy, Feisty"
date: 2007-05-24
forum: General Help
---

### Post by Skudd on 2007-05-24
Greetings everyone!

I've been running my head into a brick wall for the last couple of weeks over this issue. I have 3 project servers running Ubuntu. One was running Edgy desktop, the other two were running Edgy server. I did an 'apt-get update; apt-get -y dist-upgrade' on all three of them about 3 weeks ago, and nothing out of the ordinary was spotted. Over a couple of days, they all began to lock up randomly. I only have physical access to two of them, and I have never been able to get ANY response out of the keyboard or mouse when it happens, and the video acts like the system just went into standby mode. I have run a memtest on both local systems and verified that they are stable, and upon first glance, nothing in /var/log gives any hint as to what is causing it.

So my primary question: Were there any recent updates that would be causing this? I'm doing a fresh reload on the one project server now, and the other has been up for almost 11 days with little incident (just network headaches). I'll provide any information I can to help you better understand the situation.

Thanks!

**Edit:** I forgot to mention, two of the servers stayed online for better than 10 months before this all started.

---

### Post by Skudd on 2007-05-24
**Update:** The reinstall I was doing was with Dapper. I attempted to edit /etc/apt/sources.list to comment out the CD-ROM, and before I could even enter insert mode in vi, I had a full lockup. Video was still up, but the keyboard and mouse were entirely non-responsive. Not even a blinking light on the keyboard.

---

### Post by Skudd on 2007-05-27
**Solved:** It was all a power management issue, and was most likely caused by a faulty power supply on my one local server. Since I have completely removed it from the network, the other is running like a charm.

---

