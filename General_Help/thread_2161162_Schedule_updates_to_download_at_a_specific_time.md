---
title: "Schedule updates to download at a specific time"
date: 2013-07-09
forum: General Help
---

### Post by neilhza on 2013-07-09
Hi,

I am a complete n00b when it comes to Unix and Ubuntu, so please forgive the request below:

I need to get my ubuntu box to download all of it's updates and patches etc between say 00h15 and 05h00, as my ISP gives me loads of extra free data during this period. 
I have been browsing around, trying to work out exactly how to schedule this and came across cron jobs etc. But to be perfectly honest I get a little confused. 
Can someone please just give me a step by step guide on how to schedule this as root to download and install my updates once a week on say a Sunday night/Monday morning? 
I assume my machine would just need to be left on or is it possible to wake it from sleep to do the updates?

I have installed gnome-schedule if this makes things any easier...

Thanks for your help.

---

### Post by dino99 on 2013-07-09
you need to play with cronjob
[http://www.google.fr/#sclient=psy-ab&q=ubuntu+time+based+cronjob&oq=ubuntu+time+based+cronjob&gs_l=hp.3...1240798.1257886.3.1258196.29.20.2.7.8.0.137.1388.19j1.20.0....0...1c.1.19.psy-ab.Nxw2WPOHqVA&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925](http://www.google.fr/#sclient=psy-ab&q=ubuntu+time+based+cronjob&oq=ubuntu+time+based+cronjob&gs_l=hp.3...1240798.1257886.3.1258196.29.20.2.7.8.0.137.1388.19j1.20.0....0...1c.1.19.psy-ab.Nxw2WPOHqVA&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925)

---

### Post by Cheesehead on 2013-07-09
dino99 is right.

First, learn how to use apt-get on the command line to update your system.
Second, learn how to use apt-get's --download flag to download updates without installing them...since that's what you wrote you want to do.
Third, learn how to script all those commands together.
Finally, learn how to trigger the script using a root cron job.


Remember to document your script and cron job thoroughly. Six months from now, you may have forgotten how it all works.

---

