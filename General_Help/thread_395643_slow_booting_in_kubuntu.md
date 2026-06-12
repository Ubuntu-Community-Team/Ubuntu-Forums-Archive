---
title: "slow booting in kubuntu"
date: 2007-03-28
forum: General Help
---

### Post by Apollo101 on 2007-03-28
iam using kubuntu.
just installed it.
its boot time is more than 5mins. the hardisk light blinks with intervals. (very less)

i have 10 times more softwares in windows xp installed. it boots faster with a constant hardisk light onn.

what can be the reasong. 
is there a software that can boot it faster.?

---

### Post by bernied on 2007-03-28
Try the [bootchart](http://www.bootchart.org/) package. You can install it with apt-get or your normal package manager.

It makes charts of the boot process and should show you where the problem is.

I'm going to try it myself.

---

### Post by bernied on 2007-03-28
After installing **and rebooting**, you can find the new chart in /var/log/bootchart/

Mine is [here](http://www.tech-turtle.co.uk/edgy-20070328-1.png).

---

### Post by Apollo101 on 2007-03-28
thanks alot! :)

---

### Post by Apollo101 on 2007-03-29
Here is mine....................   [http://img164.imageshack.us/img164/751/edgy200703291lh8.png](http://img164.imageshack.us/img164/751/edgy200703291lh8.png)

can any one tell whats wrong?

---

### Post by bernied on 2007-03-30
The chart only shows 180 seconds. Does it take longer than that, or does it just feel like it?

It looks like readahead is taking 100 seconds to do whatever it is doing. [Here's](http://packages.ubuntulinux.org/dapper/admin/readahead) the package description, you might find more on google.

You might also get some info from dmesg:
```
dmesg
```
or 
```
dmesg | grep readahead
```

---

### Post by Apollo101 on 2007-03-30
some one told me it was usplash.
i uninstalled it and my boot time was now faster. i think 1min.

should i uninstall readahead too?
or are there any other apps making trouble?

---

### Post by bernied on 2007-03-30
Hmmm, I don't really know what readahead does. Some general advice though - if it works, don't fix it.

If you really want to get faster than 1 min, read through the dmesg output and try to figure out what you can do without. I'd guess though, that this will take you more time to do than all the time you save at bootup.

---

### Post by Apollo101 on 2007-04-02
ok
thank you good sir

---

