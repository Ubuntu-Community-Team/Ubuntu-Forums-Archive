---
title: "Is there still a memory leak problem with Indicator-Multiload (System Load Indicator)"
date: 2014-08-06
forum: General Help
---

### Post by Katzwinkel on 2014-08-06
I would like to have a handy indicator for my CPU and memory usage in my top panel. It seems that Indicator-Multiload (aka System Load Indicator) would be perfect for me.

However, I keep seeing reviews that state that there wre HUGE memory leak problems with this app (one example here in the forums: h[ttp://ubuntuforums.org/showthread.php?t=1951671&highlight=indicator+multiload]("http://ubuntuforums.org/showthread.php?t=1951671&highlight=indicator+multiload")). 
All of these reports come from 2012 or before that, so one could assume that this bug has been solved. However when i look into the respective bug reports at launchpad, they all state "confirmed" etc and none is solved.

So, has anybody recently (in ubuntu 14.04) experienced any memory leak problems with this tool? Is it safe to install and use?

---

### Post by grahammechanical on 2014-08-06
What do you mean by safe to install and use? I have installed it and it did not break the OS, I use it and it is not causing crashes. I installed System Load Indicator in Trusty Tahr (14.04 under development) and ran it through out the 26 week development period. I am now running System Load Indicator in Utopic Unicorn (14.10 under development). I can use top to find out how much of the system resources are being used by each running process and System Load Indicator use 0.9% of my 1GB RAM and it is consistent at doing that. When I open the Preferences panel then RAM usage goes up to 2.2%

Oh, by the way, that thread that you linked to is about hud-service using 27.5% memory and Compiz using 12% and then 25%. If you look down the  list of the top read-out you will see in both read-outs that indicator-multi-load is only using 0.2% memory. Also System Monitor is a different utility to System Load Indicator. And those top read-out show gnome-system-monitor as using 0.3%.

My system shows Compiz steady at 7% and hud-service does not show at all even when I activate the Hud.

Regards.

---

### Post by Katzwinkel on 2014-08-06
Hi grahammechanical. It's good to know that therea have not been any issues with this tool with you. I know that system monitor and system load indicator are different tools. But if you scroll down to the replies #5 and #6 of the linked thread, you'll see that they apparently traced the problem to system load indicator (which he is using as well). The poster just used the standard system monitor to better show the memory leakage situtation.
With safe to use, i mean can i let apps on my laptop run unsupervised without a danger of a similar problem occuring and my system running on overload for a long time, while i'm not there?

---

