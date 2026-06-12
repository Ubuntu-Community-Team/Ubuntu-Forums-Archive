---
title: "Speeding up Gnome/Ubuntu?"
date: 2007-07-24
forum: General Help
---

### Post by PrimoTurbo on 2007-07-24
I have always had this problem for the last 3 or 4 years, Linux and Ubuntu feel a bit sluggish and less responsive then I am used to on Windows.

I was wondering what I can do to increase the speed of Gnome/Ubuntu with out switching to a different desktop environment or distribution altogether.
[B]
The problems I notice:[/B]
Slow startup of applications.
Slow rendering of menus and applications.
High use of CPU, high spikes while rendering movement of windows and resizing.

My system specs are the following.
Pentium 4 1.6GHz
768 DDR RAM
ATI 9700 Pro with restricted drivers

I have everything installed and configured already, this is not a Video drivers issue I experience the same on default and ati restricted drivers. I have tried xubuntu and I experience less sluggish performance but still more then I am used to on Windows 2000/XP/Vista.

Any help would be appreciated.

---

### Post by 23meg on 2007-07-24
> Slow startup of applications.

Try preload and prelink, look for lighter alternatives.

> Slow rendering of menus and applications.

Use a fast theme engine and light GTK theme.

> High use of CPU, high spikes while rendering movement of windows and resizing.

Make sure your video configuration is set up to make optimal use of your video hardware. But that (important) shortcoming will probably remain until the whole GL-based X infrastructure matures and GPUs take on more 2D drawing and windowing tasks.

---

### Post by HermanAB on 2007-07-24
Uhhh, what else are you running in the background?  Have a look with 'top' and 'ps -e'.  If you have something like Apache web server running and doing nothing then that will explain it!

---

### Post by crimesaucer on 2007-07-24
I used a lot of tips from this sidux list I found. I checked most of the tips out on Google and they seemed to be used in many different guides for speeding up your system: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

I only used the tips that I felt comfortable with on my laptop.

However, I didn't agree with all of the Firefox about:config tips, I prefer to follow this guide: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

....using the 2.0.0.5 settings from this page: [http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)

and also these pages:
[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)
[http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Layout.word+select.stop+at+punctuation](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Layout.word+select.stop+at+punctuation)
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)



...also, on that sidux page, I didn't install the prelinking, does that really make a difference?

---

### Post by PrimoTurbo on 2007-07-24
My system is pretty much the default Ubuntu install.

---

### Post by crimesaucer on 2007-07-24
I found this off of digg.com: [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

and: [http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

...they basically say the same things.

This also helped a little: [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

and Swiftweasel: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)



....also, for both of my posts, they have a setting for "vm.swappiness=0" which I didn't do because I only have 512MB ram and I figured I wouldn't mess with my swap file, because sometimes I need it.

---

### Post by PrimoTurbo on 2007-07-24
crimesaucer thanks for your help I read and tried some of the guides already. Is there an inherent problem why Ubuntu is so sluggish?

---

### Post by vwbeamer on 2007-07-24
Hmmm, I got a petium 1.7 and 1 gig of ram, and Ubuntu flies on my laptop.

---

### Post by crimesaucer on 2007-07-24
> **PrimoTurbo said:**
> crimesaucer thanks for your help I read and tried some of the guides already. Is there an inherent problem why Ubuntu is so sluggish?

I've never tried ubuntu for more then a couple of hours back, in 6.0.6 and 5.10...but I found xubuntu 6.0.6 faster and I have stayed with xubuntu ever since, I love it.

I never found xubuntu slower than Xp, but I always try to make things faster and all of those first guides really helped, so did OpenDNS and Swiftwesel...now my xubuntu is so much quicker then Windows Xp.

---

### Post by 23meg on 2007-07-24
[QUOTE=PrimoTurbo]Is there an inherent problem why Ubuntu is so sluggish?[/QUOTE]

There are some bottlenecks in certain libraries and with certain hardware configurations, but things are improving fast.

I get the impression that your problem is mostly with 2D drawing operations being slow; that will be fixed by hardware accelerated X becoming standard and supported on mainstream hardware. It's a problem I've felt for a long time, but I've learned to live with it. Most 2D operations are faster in Windows and OSX, but those platforms have other bottlenecks that slow you down (such as inferior memory management and economy in Windows, bloated applications, so on) which Linux doesn't have, so in terms of daily desktop use, the speed advantage is lost.

---

### Post by ZacDavis on 2007-07-25
Try some of the tips at the links found [here]("http://linandwin.wordpress.com/2007/07/20/how-to-speed-up-ubuntu/").

---

### Post by PartisanEntity on 2007-07-25
Thread moved to a more suitable forum.

---

### Post by bumcheekcity on 2007-07-25
I had this problem with a 600Mhz/512MB machine and Xubuntu. Windows XP ran faster, it seemed, than the XFCE-based system, which i knew couldn't be right. The problem was that my video card drivers were wrong, making Xubuntu painfully slow. I updated them, and it ran like a dream.

---

### Post by PrimoTurbo on 2007-07-25
Again it's not video card drivers as I can run 3d games with full fps.

---

### Post by crimesaucer on 2007-07-25
> **ZacDavis said:**
> Try some of the tips at the links found [here]("http://linandwin.wordpress.com/2007/07/20/how-to-speed-up-ubuntu/").

That was a very good link, the problem is, that a few (almost half) of those are very old (for Dapper)...but there is a lot of real good info in most of those links, just make sure it's current.


What's good about a lot of those links, plus the links that I posted, is that they have the same tweaks for basically all of the settings like Broadband Internet, Swapping, and Concurrent Booting, so at least you know the info is correct, and you have more then one source of info to feel safe about these system tweaks.


Since I originally used this guide a while back (as well as a couple others that were on your page because all of them had the same info): [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)


And then added these ones from your page today: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

another about Local DNS: [http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)


...and this one for noatime,data=writeback and: [http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)


...and I finally tried prelinking, and I can say that my computer feels even faster now...and it was already fast.

---

