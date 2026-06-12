---
title: "16GB memory total, 2GBs free. Running Chrome, Pidgin, and Terminal"
date: 2013-08-17
forum: General Help
---

### Post by altjx on 2013-08-17
I thought I posted about this issue awhile back, but apparently I can't find it. 

I have 16GB of memory total, and according to "free -m" command, I only have 2GB available. I'm not sure what the deal is. Can someone elaborate on this for me? I'm not sure if I should be concerned or not.

Here's what I see:

```
             total       used       free     shared    buffers     cached
Mem:         16088      14266       1822          0        140      11402
-/+ buffers/cache:       2723      13365
Swap:        16265          0      16265



```

---

### Post by newbie-user on 2013-08-17
Do you have a lot of tabs open in Chrome? You have a lot of stuff stored in cache. That's not necessarily a bad thing, as your ram isn't completely filled. I'm sure you find your system still responsive. It's only a problem when you start using swap.

---

### Post by altjx on 2013-08-17
> **newbie-user said:**
> Do you have a lot of tabs open in Chrome? You have a lot of stuff stored in cache. That's not necessarily a bad thing, as your ram isn't completely filled. I'm sure you find your system still responsive. It's only a problem when you start using swap.

Only a couple of things such as Facebook, Twitter, Instagram, Linkedin, and like a few articles. Nothing that I would even think could use up half my memory. My computer is still pretty fast, but just thought I'd check this out.

---

### Post by newbie-user on 2013-08-17
Well, using ram to cache stuff is good because pulling stuff from ram is so much faster than pulling stuff off of the hard drive. These could be things like applications that you may use regularly. I wouldn't worry about it, as the OS will drop stuff from the cache if more ram is needed for other things. Think of it this way: you're just getting your money's worth by using the ram that you paid for.  =)

---

### Post by kurt18947 on 2013-08-18
I find top & free commands a little confusing because they do include cache.  I find htop(in the repositories) or system monitor easier to understand.  Htop runs in a terminal and is quite light but uses colors to differentiate RAM usage.

---

### Post by OrangeCrate on 2013-08-18
> **altjx said:**
> I thought I posted about this issue awhile back, but apparently I can't find it. 

I have 16GB of memory total, and according to "free -m" command, I only have 2GB available. I'm not sure what the deal is. Can someone elaborate on this for me? I'm not sure if I should be concerned or not.

Here's what I see:

```
             total       used       free     shared    buffers     cached
Mem:         16088      14266       1822          0        140      11402
-/+ buffers/cache:       2723      **13365**
Swap:        16265          0      16265



```


**Help! Linux ate my RAM!**

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Kevin_Arnold on 2013-08-18
> **OrangeCrate said:**
> **Help! Linux ate my RAM!**

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Cool info. I knew the basics but that explained it very well!

---

### Post by Habitual on 2013-08-18
suggestion: "free -tg"

---

