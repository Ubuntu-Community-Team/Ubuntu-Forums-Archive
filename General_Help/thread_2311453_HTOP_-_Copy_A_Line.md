---
title: "HTOP - Copy A Line?"
date: 2016-01-27
forum: General Help
---

### Post by echotech2 on 2016-01-27
Is there a way to copy a line from the "htop" display?

  (Firefox 43.0.4, Ubuntu 15.10, Pepperflash installed and work fine on other flash sites)

  Problem:  When viewing any video on CNN e.g. [http://www.cnn.com/videos/us/2016/01/27/indiana-school-bus-principal-killed-pkg.wxin]("http://www.cnn.com/videos/us/2016/01/27/indiana-school-bus-principal-killed-pkg.wxin") the video pauses/starts/pauses and after about 10 seconds Firefox does the "grey out" thing, freezes for a few seconds, and then becomes unresponsive.   Clicking to close tab or shut down Firefox results in about a five second delay then the tab closes.

  I used "htop" to see what was happening and there is a very long line, longer than the width of my screen, in "htop" that shows CPU% as high as 109%(? - quad core CPU) when the above happens and I would like to copy it for possible troubleshooting.

  Thanks......

---

### Post by vasa1 on 2016-01-27
> **echotech2 said:**
> Is there a way to copy a line from the "htop" display?

...

  I used "htop" to see what was happening and there is a very long line, longer than the width of my screen, in "htop" that shows CPU% as high as 109%(? - quad core CPU) when the above happens and I would like to copy it for possible troubleshooting.

  Thanks......

Simple `top` should be present by default. With `top`, you can use batch mode and redirect the output to a file:
```
top -b -n1 > top-output.txt
```

BTW, [http://stackoverflow.com/questions/17534591/htop-output-to-human-readable-file](http://stackoverflow.com/questions/17534591/htop-output-to-human-readable-file) and this answer in there seems interesting: [http://stackoverflow.com/a/30224271](http://stackoverflow.com/a/30224271)

> **echotech2 said:**
> ...

  (Firefox 43.0.4, Ubuntu 15.10, Pepperflash installed and work fine on other flash sites)

  Problem:  When viewing any video on CNN e.g. [http://www.cnn.com/videos/us/2016/01/27/indiana-school-bus-principal-killed-pkg.wxin]("http://www.cnn.com/videos/us/2016/01/27/indiana-school-bus-principal-killed-pkg.wxin") the video pauses/starts/pauses and after about 10 seconds Firefox does the "grey out" thing, freezes for a few seconds, and then becomes unresponsive.   Clicking to close tab or shut down Firefox results in about a five second delay then the tab closes.

...(? - quad core CPU) ...
...
I'm using Firefox 4**4** without any form of Flash. My laptop is from 2009, a Dell Inspiron Core2Duo, 4GB RAM. The video played decently for me. CPU% went up to 30% for a while but nothing untoward happened.

I have hardware acceleration turned `off` because I don't have a GPU, just integrated graphics.

---

### Post by echotech2 on 2016-01-28
....Still working on this.  I will follow up when I have a bit more time.  Being retired I'm busier than when I was working, lol.

  I noticed a couple more things:

  1) Firefox will "grey out" several (5?) minutes after being started up, but this only seems to be early in the morning and happens every day, not when Firefox is started for the rest of the day.   Checking for updates?  I say this due to next.

  2) I twice started "Software Updater" manually, several days apart and the Updater greyed out for about 3 or 4 seconds.  The Updater was run several times between these occurrences with no apparent problem.  Text in the updater was "Checking For Updates" and "Finished".  This is NOT repeatable.

  The above is probably not related to CNN problem but I thought I would throw it out there.

  To be continued...

---

