---
title: "klogd and sysklogd"
date: 2007-04-02
forum: General Help
---

### Post by El_Matthews on 2007-04-02
Hello,

what's the difference between those daemons. Both have the same description in services (Keeps a log of your computer activity)

---

### Post by zach141 on 2007-09-20
I also would like to know--what are klogd and sysklogd?

Thanks.

Zach

---

### Post by SpiritIsReality on 2007-09-20
howdy
does 
man klogd
man sysklogd
help?

trails

---

### Post by zach141 on 2007-09-21
Yes, that helps quite a bit.  I'm new enough that I still forget "man".

However, what I really am asking is, do I need a system logger (at all) for a normal, non-networked home PC?

Thanks.

Zach

---

### Post by SpiritIsReality on 2007-09-21
howdy

sorry about the 4 hours pard.
you got me there. have to crunch a few searches and get back to you.

trails

(until I saw this post, I didn't even know they existed, let alone how to spell them)
if you've got a non-critical experienced(older) pc with linux, you could find out
the hard way?

---

### Post by SpiritIsReality on 2007-09-21
from machoo02 here
[http://ubuntuforums.org/showthread.php?t=484846&page=2](http://ubuntuforums.org/showthread.php?t=484846&page=2)
(I'm not any good at targeting yet)
this:
[http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)

other than that there's searches, I'll leave the diggin' to you
[http://www.google.ca/search?hl=en&q=linux+sysklogd&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+sysklogd&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+klogd&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+klogd&btnG=Google+Search&meta=)
[http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=sysklogd&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgXDIyVwJdHSzUldCqJQVcQsU2YNTKRNpYghQe33ffwGwfJk9LGiyp52hdvVNHuXPu-qvZy_vTEgyHyN-srPbhDtx0NNt1gDqUWDK3LbY9DYv3lyK5kQXlgXg_5J-N37Km--c15Bmv1MdDNopLP-cixN9fucbw51GcOGbUOdn0uSuOediRK1Q_Elj9xlo6vUg0lWDQRuhrdGGmI8td2lc1y3u25FnQ&client=pub-7825705102693166&channel=3833691868](http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=sysklogd&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgXDIyVwJdHSzUldCqJQVcQsU2YNTKRNpYghQe33ffwGwfJk9LGiyp52hdvVNHuXPu-qvZy_vTEgyHyN-srPbhDtx0NNt1gDqUWDK3LbY9DYv3lyK5kQXlgXg_5J-N37Km--c15Bmv1MdDNopLP-cixN9fucbw51GcOGbUOdn0uSuOediRK1Q_Elj9xlo6vUg0lWDQRuhrdGGmI8td2lc1y3u25FnQ&client=pub-7825705102693166&channel=3833691868)
[http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=klogd&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgWCC4Y9IPRGcMkBYfq-yGzc1FeUiROmkrB0v7oyiNMP6V0GRZdLaDUNkZieHfY12kHBAwAK7cMQPd2sIZZkT8fLIPS6Yb9gbezo3Thg_AMvRaDtugwWx0TghJFiIfgpFhePM8sMCq1gPPB5GCUr-Z96BCNksFQaKJ5YokJGv103e_s8h-NlD0abTKVvrvILjawA_bVMVwpzKSqybyTSoFrSlChhqw&client=pub-7825705102693166&channel=3833691868](http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=klogd&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgWCC4Y9IPRGcMkBYfq-yGzc1FeUiROmkrB0v7oyiNMP6V0GRZdLaDUNkZieHfY12kHBAwAK7cMQPd2sIZZkT8fLIPS6Yb9gbezo3Thg_AMvRaDtugwWx0TghJFiIfgpFhePM8sMCq1gPPB5GCUr-Z96BCNksFQaKJ5YokJGv103e_s8h-NlD0abTKVvrvILjawA_bVMVwpzKSqybyTSoFrSlChhqw&client=pub-7825705102693166&channel=3833691868)
[http://www.google.ca/search?hl=en&q=linux+kernel+handbook&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+kernel+handbook&btnG=Google+Search&meta=)

I'll go back to reading now
"ubuntu linux bible"

trails

---

### Post by zach141 on 2007-09-21
You offered quite a bit of reading; I'll get to work.

And yes, this is an old PC rejuvenated with Ubuntu--my PC's limited resources would be why I do care if an unnecessary process is running on it.  For example, do I really need both? (the literature I've hit so far seems to say one builds on the the other.)  

Zach

---

### Post by SpiritIsReality on 2007-09-21
howdy
I've got a pentium 2 and a pentium 3, and I never once thought of what you're doing.
good for you, but I don't mean for you to do a lot of reading on my account. try a post
to a lug(linux user's group) or something, irc channel, click on the rss feeds at the top
of this page? if you don't mind re-installing if you have to, try deleting one of them and
see if your rig bucks you off, or it doesn't mind?
you're in the saddle

trails

---

### Post by zach141 on 2007-09-22
Okay, I think I'm good with the system loggers now.  I don't think you understood just how basic my question was (how low my general knowledge level is!) :)   

I'm embarrassed to say I had to go to The Evil Empire to understand.  System loggers (I think) provide info roughly equivalent to that found in "Computer Management" in Windows XP.  Although, I don't presently know how to access that info in Ubuntu, I'm sure I (or someone) could get it if needed to repair something.

So, to ensure that there is a log to reference what might happen, I'll go back and turn klogd and sysklogd back on.  Like I said, it's old--a 1998 Compaq with a 12-gig harddrive and a Celeron chip!  And it does quite well with the Ubuntu; I was just trying to conserve machine resources.

So--Thanks.

Zach

---

### Post by SpiritIsReality on 2007-09-22
ok good to hear.

there's kind of a road map here
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
and then there's aboutdebian.com
[http://aboutdebian.com/](http://aboutdebian.com/)

happy trails

---

