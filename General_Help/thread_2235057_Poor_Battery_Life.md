---
title: "Poor Battery Life"
date: 2014-07-18
forum: General Help
---

### Post by mike215 on 2014-07-18
Just installed 14.04 on my Asus X502C notebook without a hitch. Only problem I am running into is that the battery life is noticeably worse than when I was running Windows. After doing a bit of searching I've seen a few different answers and sure sure which is best given my notebook. I attached a screenshot with my system info if that helps. Thanks in advance

---

### Post by sp40140 on 2014-07-18
Try installing power management tool: TLP. See, if it helps.
How to:
$ sudo add-apt-repository ppa:linrunner/tlp
$ sudo apt-get update
$ sudo apt-get install tlp tlp-rdw

---

### Post by mike215 on 2014-07-18
Got TLP up and running as far as I can see, will post back here if it works, thanks!

---

### Post by mike215 on 2014-07-20
So I've tried to see an improvement with TLP but I don't think its really making a change. Are there any other options that I can explore, or any system changes I can make with my setting to stop using so much battery? It's dropping about a percent every minute or two...

---

### Post by sp40140 on 2014-07-21
In that case it could very well be caused by drivers. I will stop here and let smarter people help you.

---

### Post by Mark Phelps on 2014-07-21
There used to be an app known as Jupiter which was often used to deal with these situations of overheating and resulting excessive battery drain -- but that project has been abandoned. Like others, I recommend tlp in its place -- which you're already tried.

Unfortunately, on laptops, Windows generally now does a better job of processor idling than does Linux.

Hopefully, someone will come along with a solution, but at this point, I think you're stuck.

---

### Post by mike215 on 2014-07-22
Thanks for all the input, guys. I'll be tinkering away and will come back with whatever I find to work if I can.

---

