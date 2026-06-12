---
title: "What is RAID do I need it and how do I know if its installed"
date: 2013-04-03
forum: General Help
---

### Post by Grafens on 2013-04-03
As the title says. Also what’s the difference between hardware and software Raid arrays


Thanks

---

### Post by slickymaster on 2013-04-03
Believe it or not, in webopedia there's one place that answer all your questions in just a page.

Check it out: [RAID - redundant array of independent disks]("http://www.webopedia.com/TERM/R/RAID.html")

Edit: So I won't be later on accused of not mentioning it, there's also one at wikipedia that does the same. Check it [here]("http://en.wikipedia.org/wiki/RAID").

---

### Post by Grafens on 2013-04-03
Thanks for the links turns out that I don't need it, how do I know if ubuntu installed or not.

---

### Post by slickymaster on 2013-04-03
I'm not sure I understand your post correctly
 
In any case I think this is a good place for you to start: [Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

---

### Post by Grafens on 2013-04-03
ahh I meant to say 'installed it or not'
For those interested 
> cat /proc/mdstat
will tell you if you have RAID up and running.
Anyway I'm trying to find out why this folder '/dev/mapper/fedora_ld-root' exists inside ubuntu. [http://ubuntuforums.org/showthread.php?t=2131724&p=12585407#post12585407](http://ubuntuforums.org/showthread.php?t=2131724&p=12585407#post12585407)
Suppose I should ask over at the boot-repair thread


Thanks again for the links

---

### Post by steeldriver on 2013-04-03
that could be because your fedora installation was done with LVM instead of traditional partitioning

---

