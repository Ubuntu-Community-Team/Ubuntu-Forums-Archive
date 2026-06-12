---
title: "What's with swap?"
date: 2008-05-07
forum: General Help
---

### Post by trogdor282 on 2008-05-07
So I have a laptop with 1gb ram. If I keep it on for a while, linux fills up my whole ram with disk cache. From [this thread]("http://ubuntuforums.org/showthread.php?t=393014") I understand that's normal. But the part I don't get is once my ram fills up with cache, the swapfile starts going like crazy! I open a new tab in firefox and I have to wait 10 seconds while the system thrashes the swap like crazy.

I stuck in another 2gig stick. Felt great for a while, but as soon as it filled up with cache, BAM, thrashing again!

So, by trial and error I found that disabling swap entirely is the solution. So my question is, if swap and cache are supposed to speed up my system, *why do they instead slow it to a crawl*?

---

### Post by bodhi.zazen on 2008-05-07
Swap does not speed up your system. Swap is essentially using hard drive space for RAM when you run out of RAM.

Either you have an application with a memory leak, may well be firefox, or you are using a lot of memory intense applicaions.

You can reduce the likely hood your system will use swap by adjusting swappiness.

To see your current swapiness :

```
sudo sysctl -q vm.swappiness
```

The default is 60

Set swapiness with 

```
sudo sysctl vm.swappiness=0
```

This will reduce the likely hood you system will use swap.

If you like this setting :

```
gksu gedit /etc/sysctl.conf
```

Add this line :

```
vm.swappiness=0
```

Save and exit. Swappiness is not set at 0 and will be set at 0 when bootine (without this edit it will revert to 60 with rebooting).

You can then leave your swap partition. This is better as if you actually run out of RAM your system will crash, possibly with data loss.

---

### Post by HermanAB on 2008-05-07
Yah, it is Firefox.  If you want to run a system without /swap (ferinstance on an Eee PC), then you should refrain from using buggy applications like Firefox.

---

### Post by trogdor282 on 2008-05-07
> **bodhi.zazen said:**
> Swap does not speed up your system. Swap is essentially using hard drive space for RAM when you run out of RAM.

Yeah, I understand that. My question is why I'm waiting for swap at all when I have 3gigs of ram and only 500 megs of it is being used. I feel like the default behavior should be shaving down the 2.5 gigabyte disk-cache instead of resorting to swap so fast.

But I didn't know about 'swappiness', I'll def check it out.

---

### Post by trogdor282 on 2008-05-07
> **HermanAB said:**
> Yah, it is Firefox.  If you want to run a system without /swap (ferinstance on an Eee PC), then you should refrain from using buggy applications like Firefox.

It's nothing to do with firefox. That was just an example. Here's with firefox closed:

```
frieko@lappy:~$ top
top - 11:38:05 up 20:14,  1 user,  load average: 0.11, 0.41, 0.77
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.5%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3088148k total,  2882216k used,   205932k free,    47464k buffers
Swap:        0k total,        0k used,        0k free,  2217044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
16527 frieko    20   0  310m 120m  21m S    1  4.0   2:22.84 ktorrent
 5317 root      20   0  488m  80m 5600 S    1  2.7  21:19.47 Xorg
19412 frieko    20   0  121m  58m  31m S    0  1.9   0:17.94 ld-linux.so.2
21173 frieko    20   0  239m  52m  21m S    0  1.7   0:17.04 systemsettings
 6119 frieko    20   0  474m  43m  25m S    0  1.5   2:06.76 pidgin
 6047 frieko    20   0  227m  38m  26m S    0  1.3   0:45.12 guidance-power-
 6011 frieko    20   0  181m  28m  12m S    0  1.0   0:13.22 kdesktop
 6052 frieko    20   0  216m  26m  14m S    0  0.9   0:01.24 python
 6013 frieko    20   0  200m  22m  15m S    0  0.7   0:21.46 kicker
16284 frieko    20   0  193m  22m  16m S    0  0.7   0:00.40 konqueror
 5259 root      20   0  134m  21m 2004 S    0  0.7   0:45.92 NetworkManager
 6127 frieko    20   0  168m  20m  11m S    0  0.7   0:04.86 adept_notifier
 6252 frieko    20   0  159m  19m  13m S    0  0.6   0:00.18 gpmhelper.py
22834 frieko    20   0  166m  17m  12m S    0  0.6   0:01.08 konsole
 6001 frieko    20   0  203m  16m  11m S    0  0.5   0:15.34 kded
 6058 frieko    20   0  165m  15m 9328 S    0  0.5   0:00.14 kblueplugd
14261 frieko    20   0  165m  15m  10m S    0  0.5   0:00.56 kmix

```

---

### Post by wdaniels on 2008-05-07
This is basically showing 2.2Gb of available RAM and swap disabled.  So are you saying that you have heavy disk I/O going on under those circumstances that you can't attribute to an application?  What makes you think it's swap activity?

---

### Post by trogdor282 on 2008-05-07
> **wdaniels said:**
> What makes you think it's swap activity?

Because disabling swap solved the problem.

---

### Post by wdaniels on 2008-05-07
> **trogdor282 said:**
> My question is why I'm waiting for swap at all when I have 3gigs of ram and only 500 megs of it is being used. I feel like the default behavior should be shaving down the 2.5 gigabyte disk-cache

That's generally what should happen, unless there is a lot of *inactive* RAM being used by applications.  As already mentioned, the tendency to swap instead of reclaiming from the cache can be adjusted by the swapinness variable, which is 60 by default, i.e. it slightly favours swapping out inactive pages.  But this is also balanced between the length of time the application pages have been inactive and the time since disk cache pages were hit.  So if you were finding a lot of application stuff getting swapped out, then the disk cache must have been performing well in the meantime if there was relatively little in that 2GB or so that was used longer ago than the application.

The rationale here is that you were presumably benefiting from much increased disk performance during the time since you last used the application, and it's this level of caching that can sometimes show extraordinary performance benefits for linux against other platforms.  As an example, I found that running a certain Windows game which had a large (>1GB) flat file resource database, was significantly faster on linux, even running through Wine, rather than Windows on the same hardware.

What is quite the best balance to use for default has always been the subject of debate and I wouldn't want to comment on whether the current default is a good one or not (other than perhaps to say that it works well for me personally), but I hope to have helped answer the question by explaining some of the logic behind it.

---

### Post by trogdor282 on 2008-05-07
> **wdaniels said:**
> I hope to have helped answer the question by explaining some of the logic behind it.

Yeah! That really does answer my question, thanks!

---

### Post by wdaniels on 2008-05-08
> **wdaniels said:**
> the tendency to swap instead of reclaiming from the cache can be adjusted by the swapinness variable, which is 60 by default, i.e. it slightly favours swapping out inactive pages.

It's been a while since I last read up on all this stuff, so I decided to do a little research just now, and I have to correct myself slightly.  The way the swappiness parameter is applied is not quite as simple as I thought, it is actually used as a modifier in addition to the percentage of memory allocated to applications (mapped_ratio), and the current level of demand for memory that is not immediately available (distress):

```
swap_tendency = mapped_ratio/2 + distress + vm_swappiness;
```

For all the details of this there is an excellent article [here]("http://lwn.net/Articles/83588/").  It sounds like there might be some work in 2.7 to improve the criteria used to select *which* pages to swap, rather than just recency of activity, which should help improve the situation somewhat, but I haven't looked into any of that yet.

---

