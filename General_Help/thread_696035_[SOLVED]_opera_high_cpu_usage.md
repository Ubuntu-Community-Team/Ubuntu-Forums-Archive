---
title: "[SOLVED] opera high cpu usage"
date: 2008-02-13
forum: General Help
---

### Post by trash on 2008-02-13
It hasn't bothered me in the past but lately I need to restart Opera quite often as it starts hogging resourses.. 45-50% cpu usage is a but rediculous lol. Anybody else experiencing this? I am using 9.50 beta 1

---

### Post by rich257 on 2008-02-13
This happens to me when there is Flash content on a page, which is almost all pages, certainly those with ads.  I suspect the CPU usage is at 50% because you have a dual core processor and Opera is using 100% of one core.  For me the CPU usage reduces after a while.  While Opera and Flash only "tolerate" each other on Linux there is no solution as far as I know.

---

### Post by trash on 2008-02-13
Ya you're right, i guess i never waited long enough to see it go back down to normal... I see 50% usage and just kill whatever it is if i'm not using it:lolflag:

---

### Post by .nedberg on 2008-02-21
I _think_ it is a known problem with 9.50b, it will probably be fixed before the final release. There is a new weekly tomorrow (friday 22. feb), hopefully it will fix the plug in problem with Opera and Linux...

---

### Post by Crafty Kisses on 2008-02-21
I don't have that much trouble with Opera, post the following output: ```
top
```

---

### Post by .nedberg on 2008-02-22
```


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9660 even      34  19 78100  22m  13m R 25.3  1.1   0:04.99 operapluginwrap

```

When I have 4 tabs open, one showing a Youtube video. I am pretty sure this is a known issue with Opera 9.5b (Kestrel builds) and Flash. This is not present with 9.26 witch is the latest stable version.

CPU usage changes from 25~50%.

A quick look at the desktopteam blog showed me that this has been reported a lot of times in the comments on Kestrel builds.

I am hoping for a new build today that will fix the plug in crashes of the latest weeklies!

---

### Post by ingrid_ozikem on 2008-05-28
I don't see how this problem was solved here.. I downloaded Opera 9.50 Beta 1 just now (almost June'08) and the operapluginwrap hogs 70 - 80% of the CPU while playing flash.

Of course, Firefox 3 also does the same thing.. so how can I watch flash without overheating my poor laptop ?

has anyone gotten around this?

---

### Post by .nedberg on 2008-05-28
> **ingrid_ozikem said:**
> I don't see how this problem was solved here.. I downloaded Opera 9.50 Beta 1 just now (almost June'08)

Why beta 1? Beta 2 has been released... Get it at [http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2)

---

### Post by ingrid_ozikem on 2008-05-29
Strange.. I downloaded the most prominent version from the website just 2 days ago and Help -> About in Opera claimed "Beta 1".  I followed your link and now it does say "beta 2" though installation seemed to take barely a moment. Thanks though!!

I notice that viewing flash (say youtube) still sends operaflashplug and Xorg total CPU use to 85 - 90%..  is this even considered a bug anymore or is it just what it takes to view flash in linux?

---

