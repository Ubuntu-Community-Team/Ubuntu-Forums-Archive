---
title: "Monitor Internet bandwidth"
date: 2013-11-25
forum: General Help
---

### Post by sarahfoxnz on 2013-11-25
Hello. I've just downloaded VNSTAT to monitor my internet traffic. Its good (so far), but is on a command-line basis.

i have a few queries.

1) Does VNStat monitor the traffic for MY PC ?  or all / any devices connected to my wifi modem ?  (1 other person uses wi-fi.. )
(a Thomson gateway 585 modem.)

i'm wondering if its possile to monitor how much each /all the devices use on a combined or individual basis.

2) is/are there any graphic / auto-updated monitors available that i dont need to use command-line to use ?

EDIT:

3) my wifi is active 24/7, but not "my" Pc - If i turn off my PC, & turn it on a few hours later (when i come home at night), will VNstat still record / show me the traffic usage while the Pc is off ? (The other person / devices are still active & may use traffic)

EDIT 2 - Modem is Thomson Gateway 585 (not 525) -   TG585 v8

---

### Post by Kirboosy on 2013-11-25
1. I think unless you have your entire network traffic routing through  the vnStat enabled box you will only be sniffing your traffic on that  particular box. From the jist of what I have read about it > vnStat  won't actually be sniffing any traffic and also ensures light use of  system resources.
I have yet to find anything that would state otherwise.

2. I don't know much about vnStat but I did manage to find a front end that you can use to have a nice report of your network. [vnStat PHP frontend]("http://www.sqweek.com/sqweek/?p=1")   You may want to take a look at anther network monitor called [ntopng]("http://www.ntop.org/products/ntop/") and see if that is more what you are looking for.

3. If you shutdown your monitoring computer you will lose the ability to monitor the network. You may want to check to see if your modem supports logging the network activity. That might be the easiest solution. Another alternative would be to buy a router that will allow you to monitor all the network traffic and log it.

Hope that helps!
~Caboose

---

