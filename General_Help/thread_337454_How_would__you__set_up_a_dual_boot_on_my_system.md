---
title: "How would _you_ set up a dual boot on my system?"
date: 2007-01-13
forum: General Help
---

### Post by DGoose on 2007-01-13
I'm looking for opinions here. I have three physical HDDs: 6GB, 10GB, 160GB.

Current Set Up:
6GB - Unused (Used to be Fedora Core 5)
10GB - fat32
160GB - 130GB XP Installation; 30GB ntfs

Result Wanted:
6GB - Ubuntu Installation
10GB - XP Installation
160GB - 80GB for Ubuntu 6.06 and 80GB for XP

The final result is easy. What I'm looking for is a process that will get me there with what I want with fewest hassles. 

I would like my existing XP installation transfered to to the _much_ smaller drive, preferably keeping my settings intact. If a direct transfer isn't feasible I'll just do a clean install on the smaller drive and use XP's files and settings transfer wizard.

Another problem is I estimate I have at least 50 gigs worth of data I'd like to keep. Would back up software be necessary or would QTParted be able to get the results I desire?

I'm not afraid of screwing my system up. If I accidentally lose everything, I'll get over it. I just don't have the willpower to intentionally erase everything and start from scratch.

Any relevant response welcomed and appreciated, and if you need more info or clarifications just ask.

Thanks,
  --DGoose

---

### Post by dbd on 2007-01-13
I'm not sure how to transfer an XP install from one drive to another without losing settings, but I'm sure it must be possible. If I was gonna try something without googling around first I'd do a fresh XP install on the 10Gb and then overwrite the windows data with that from the old install.
However, it is a good idea to reinstall XP at least every 12 months anyway, or it gets slow and starts going wrong. So I'd recommed just doing a totally fresh install.

As for your 50Gb of data you should be ok with QParted, however there is always the risk of losing it. I'd back up the important stuff first (possibly to the other drives).
Also when resizing such a big partition, I'd avoid doing that with the Live disk, and would use an Ubuntu already installed. I've never heard of anyone else advise this, but it seems safer to me.

So here is what I'd do if I were in your position:
1) Install XP on 10Gb drive
2) Install Ubuntu on 6Gb drive
3) Backup important data from 160Gb drive (poss to other drives)
4) Copy other wanted data from 30Gb partition to 130Gb partition.
5) Using Ubuntu delete 30Gb partition, shrink 130Gb partition and make new partition for Ubuntu.

Good luck :)

---

