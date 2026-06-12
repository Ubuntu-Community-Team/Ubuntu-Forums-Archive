---
title: "Firefox causes IOWait every pageclick"
date: 2013-06-20
forum: General Help
---

### Post by m1dnight on 2013-06-20
Hello,


I'm running a fairly new installation of ubuntu 13.04. I'm using firefox and since today it started behavind oddly.

The issue here is that whenever I open a page in firefox it causes an IOWait of about a second or 2. It's seems to be correlated to the loadtime of the page. This makes my entire laptop unresponsive for a few seconds.

I've been investigating this issue and found that firefox writes a lot of data to my harddrive. I thought it could be sessionstore so I wanted to turn that off. This does not seem possible in Firefox 21.

Could anyone help me with this issue please?

---

### Post by tgalati4 on 2013-06-20
What are the SMART parameters of the disk drive?  IOWaits can happen when a drive is failing and it takes a long time to get corrected, sector reads.  You can clear the cache and see if that speeds up firefox.  If the cache gets too big it can slow down the browser performance.

---

### Post by m1dnight on 2013-06-21
Okay, I've installed smartctl and I will run a test today. I'll get back with the results. Thanks!

So here is the result:

I've put it in a [file]("http://begijnhof.no-ip.org:8080/Shared/Overige/smartresult.txt") for a bit more readability.

I can't seem to find anything suspicious in the report. Also, shouldn't i have the symptoms in other application, or in general?

Okay, So i've been trying to enable/disable anything that has to do with a diskwrite/read in firefox. Here's what I've done:

browser.cache.disk.enable;false
browser.cache.disk.smart_size.first_run;false
browser.cache.disk.smart_size.use_old_max;false
browser.cache.disk_cache_ssl;false
browser.cache.disk.max_entry_size;10

There is definitely improvement! The i can open a webpage or 5/6 and then it's like the IO wait is there with a delay for those pages :) But it's somewhat workable now. Not that I'm going to use Firefox instead of Chrome, but I'd like to get this figured out.

I also did what you said, trying to clear the cache.Thad had no apparent effect on the situation.

Another thing I tried was disabling all add-ons, but that didn't help either.

---

