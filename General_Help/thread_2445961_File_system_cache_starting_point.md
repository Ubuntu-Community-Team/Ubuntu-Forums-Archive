---
title: "File system cache starting point"
date: 2020-06-22
forum: General Help
---

### Post by yaminb on 2020-06-22
I'm looking for a starting point on what package/product to look at in terms of file system caching.
Keep in mind, a lot of this is purely my own interest. I know I could just get another SSD drive or something like that.
I just have a genuine interest in what's out there at times and playing with things.

My setup:
500 GB SSD with ubuntu
2 TB HD with various partitons (Windows...)

My need:
I'd like to investigate setting up a cache on the SSD for the HD.

My ideal:
I setup a 50 GB file on the SSD to act as the cache. I'd like to avoid repartition if possible
I setup the cache so if it's trying to read a file off the HD, it checks the cache first
I'd like to play with rules, like only put files > 5 MB in the cache or something like that.

Is there a reliable package or program out there that exists that does something like this?

---

### Post by ActionParsnip on 2020-06-22
You can possibly resize the Ext4 i gparted. If you boot to live CD then you can do this

---

### Post by oldfred on 2020-06-22
Understand even SSD is orders of magnitude slower than RAM. And Linux caches your activity into RAM automatically.

Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)

---

