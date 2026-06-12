---
title: "How to fix excessive memory usage?"
date: 2012-11-20
forum: General Help
---

### Post by tdp2010 on 2012-11-20
Lately I've been noticing that my system has been using up a lot more memory than it should be - I'm running Xubuntu 10.04.  When I first boot up, there's usually from 110-130 MB used.  Once I add Firefox and Opera to that, with multiple tabs open in each, memory usage goes up to around 480 MB.  However, once I close those out after a few hours, used memory only drops to about 250 MB.  All the processes running in the background are taking up about 30 MB at that point.  So I'm missing a good chunk of memory here, presumably lost to the cache.  But shouldn't the cache clear itself when the programs that filled it are shut down?  Or is there something else here I'm missing?

Anyway, I'd really appreciate any suggestions on how to get this missing memory back.  I've only got 1 GB to work with at the moment, so even otherwise small gains are useful.

---

### Post by syerges on 2012-11-20
My suggestion is to do what I did... start over with Lubuntu as it uses the least amount of resources and only install what you need afterwards. I didn't do it because I had restrictions but because I do alot of conversions of large files and wanted to maximize productivity.

---

### Post by ibjsb4 on 2012-11-20
Are you sure its a problem?

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by syerges on 2012-11-20
> **ibjsb4 said:**
> Are you sure its a problem?

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

You can also give your system more memory to cache if things are lagging.

---

### Post by efflandt on 2012-11-20
Programs and files read or written to disk are buffered or cached, so if you need them again, they are much more quickly available from RAM instead of having to be reread from your slower hard drive.  But RAM used for cache is not really tied up, it will automatically be freed up if you need it to run programs.

Sometimes a particular program can have a memory leak that can result in it constantly growing, but they usually try to sort that out before release, and 10.04 has been around for a long time.  Although, it is possible for a 3rd party or java program to have a memory leak.

Not sure how you are determining memory use, but the **free** command in a terminal can tell you not only how much you are currently using for programs, buffers, and cache, but also how much is available if you need it from buffers and cache.  To see it in megabytes use **free -m**

If you are trying to judge it from **ps aux** or other method of looking at running processes, some related processes share the same memory.

---

### Post by black veils on 2012-11-22
that seems like expected behaviour to me.

try this, where it has the header **"then do this tweak"**  [http://ubuntuforums.org/showpost.php?p=12261874&postcount=2](http://ubuntuforums.org/showpost.php?p=12261874&postcount=2)
this should help a lot with your performance, you may also want to try a smaller number, maybe 7 or less. but see how you are with 10. and quit staring at your ram usage :P

change the types of applications you use. one trick for casual web browsing is to use midori in iphone mode.

or, as suggested, use lubuntu instead (or wattos, it is very fast).

---

### Post by ibjsb4 on 2012-11-22
> **black veils said:**
> that seems like expected behaviour to me.

try this, where it has the header **"then do this tweak"**  [http://ubuntuforums.org/showpost.php?p=12261874&postcount=2](http://ubuntuforums.org/showpost.php?p=12261874&postcount=2)
this should help a lot with your performance, you may also want to try a smaller number, maybe 7 or less. but see how you are with 10. and quit staring at your ram usage :P

change the types of applications you use. one trick for casual web browsing is to use midori in iphone mode.

or, as suggested, use lubuntu instead (or wattos, it is very fast).

How does any of that explain "excessive memory usage" ??

Your post reads more like spam.

---

### Post by snowpine on 2012-11-22
> **tdp2010 said:**
> Lately I've been noticing that my system has been using up a lot more memory than it should be - I'm running Xubuntu 10.04.  When I first boot up, there's usually from 110-130 MB used.  Once I add Firefox and Opera to that, with multiple tabs open in each, memory usage goes up to around 480 MB.  However, once I close those out after a few hours, used memory only drops to about 250 MB.  All the processes running in the background are taking up about 30 MB at that point.  So I'm missing a good chunk of memory here, presumably lost to the cache.  But shouldn't the cache clear itself when the programs that filled it are shut down?  Or is there something else here I'm missing?

Anyway, I'd really appreciate any suggestions on how to get this missing memory back.  I've only got 1 GB to work with at the moment, so even otherwise small gains are useful.

RAM is like a bucket. So long as the water fits in the bucket, the bucket will not overflow.

You have 1GB RAM and are only using 480mb at the maximum, so there is no problem. :)

---

