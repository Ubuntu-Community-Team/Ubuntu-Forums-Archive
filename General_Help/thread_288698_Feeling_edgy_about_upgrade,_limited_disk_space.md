---
title: "Feeling edgy about upgrade, limited disk space"
date: 2006-10-30
forum: General Help
---

### Post by Zeroangel on 2006-10-30
Hi all,

I have 1.2 gigs free on my main partition, however the dist-upgrade to Kubuntu edgy will require me to download 942MB of archive and will end up taking up ~350MB of extra space.

I would just like to know if it's safe to upgrade via dist-upgrade even with the limited space.

Is it?

---

### Post by Sef on 2006-10-30
I would suggest not if you're that tight on space.  I had a problem once where I didn't have enough space and could not boot up.

---

### Post by Zeroangel on 2006-10-31
Thanks for the response. However, after freeing some 600MB of data I ran the dist-upgrade.

Install says it will need to download packages and the new packages will take up x amount of space, making it ( 950M + 350M = 1.3G ) Well, with 1.8G free, I went ahead with the install.

I checked the free space every once in awhile throughout the upgrade. I assumed that the system would need a rather huge berth for tempfiles and the like, but it actually didnt. The 'used space' for the upgrade process stayed pretty much constant after the packages were downloaded and took up 1.3G just like the installer predicted.

I thought this might be useful to anyone else who has low disk-space.

---

### Post by scott_b on 2006-10-31
Thanks for the post. 

do you know how the old files are handled after an upgrade? are they deleted? can they be deleted?

---

### Post by Zeroangel on 2006-11-01
Not automatically, but you can delete them by running the command
```
sudo apt-get clean
```and all of the cached files will be cleaned up, giving you back most of the space you had prior to the upgrade.

---

### Post by SqRt7744 on 2008-04-10
I'm going to be upgrading from gutsy to hardy on an eee soon - the OS partition has 315 MB free. I think the way to do it is to link /var/cache/apt/archives to an external disk for the upgrade process so that the dowloaded deb files aern't consuming all the available working space. ...or I may just do clean install so I can consolidate the partitions, haven't decided yet.

---

