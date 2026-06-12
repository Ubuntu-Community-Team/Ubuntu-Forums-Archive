---
title: "Ubuntu screwing up Hardware Clock"
date: 2008-02-29
forum: General Help
---

### Post by tsali on 2008-02-29
Ubuntu is screwing up my hardware clock. I dual boot with Windows. Every time I boot into Ubuntu, then boot back into Windows, the hardware clock is off by 6 hours.

How do I stop this? I never gave Ubuntu permission to change my system setting like this.

---

### Post by WakkiTabakki on 2008-02-29
In Ubuntu, make sure:
1. Its configured to be in the correct time zone (System/Admin/Time and Date)
2. Right click the clock in the top panel and choose properties. Make sure 'Use UTC' is NOT checked

/N

---

### Post by zveroboy on 2008-03-10
An answer in a different thread worked for me:
here is a link:
[http://ubuntuforums.org/showthread.php?t=708519&highlight=hardware+clock](http://ubuntuforums.org/showthread.php?t=708519&highlight=hardware+clock)

and here is the post:
> 
[http://www.arsgeek.com/?p=863](http://www.arsgeek.com/?p=863)



This is from that article.



sudo cp /etc/default/rcS /etc/default/rcS.bak



gksudo gedit /etc/default/rcS



Look for the line that says:



UTC=yes



and change it to:



UTC=no



Now, save the file and go to System -> Administration -> Time and Date and set your info to the correct time and date.



Lastly let&#8217;s restart the hardware clock



sudo /etc/init.d/hwclock.sh restart



You should be at the correct time and date now.



I hope this helps 





Thanks to Envirotech for posting this.

---

