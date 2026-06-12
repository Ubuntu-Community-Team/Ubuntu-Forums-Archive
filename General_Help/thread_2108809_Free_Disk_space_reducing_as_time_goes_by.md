---
title: "Free Disk space reducing as time goes by"
date: 2013-01-25
forum: General Help
---

### Post by matimont on 2013-01-25
Hi,

I have an Ubuntu VPS (Ubuntu 12.04) and noticed I had 50% of my disk space used when I started it. 4 months later, I have 65% of my disk space used and I have not really added much stuff, where can I look to free up disk space? Is there a tool I can run? It may be logs growing?

Thank you!

---

### Post by TheFu on 2013-01-25
df
du

Read the man pages for some great options.

---

### Post by mattyasaurus on 2013-01-25
> **matimont said:**
> Hi,

I have an Ubuntu VPS (Ubuntu 12.04) and noticed I had 50% of my disk space used when I started it. 4 months later, I have 65% of my disk space used and I have not really added much stuff, where can I look to free up disk space? Is there a tool I can run? It may be logs growing?

Thank you!

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) 
Take a look at: Remove partial packages, Remove unnecessary locale date, Remove "orphaned" packages...

```
sudo apt-get autoclean 
sudo apt-get install localepurge 
sudo apt-get install deborphan 
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by mattyasaurus on 2013-01-25
> **matimont said:**
> Hi,

I have an Ubuntu VPS (Ubuntu 12.04) and noticed I had 50% of my disk space used when I started it. 4 months later, I have 65% of my disk space used and I have not really added much stuff, where can I look to free up disk space? Is there a tool I can run? It may be logs growing?

Thank you!

you could check out this page too, it has helped me out in the past
[http://mangstacular.blogspot.co.uk/2011/03/freeing-hard-disk-space-in-ubuntu-linux.html](http://mangstacular.blogspot.co.uk/2011/03/freeing-hard-disk-space-in-ubuntu-linux.html)

---

