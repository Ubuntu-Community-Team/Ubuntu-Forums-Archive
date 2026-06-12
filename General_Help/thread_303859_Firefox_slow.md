---
title: "Firefox slow"
date: 2006-11-20
forum: General Help
---

### Post by juantovarm on 2006-11-20
Whenever a link is opened in a new page it takes around 10 seconds for firefox to open, my computer gets real slow and nothing works... until firefox finally agrees to open the new page. This doesn't happen if it opens the page in a new tab, only in a new navigator window...

any ideas?:-k

---

### Post by macogw on 2006-11-21
I think it has to start a cache and a whole new instance of Firefox to open in a new window, so it's like when FF first starts up.  Just set it to open links from other programs in new tabs and open links that are set to "new window" in the html to switch over to tabs too (it's in preferences).

---

### Post by janfsd on 2006-12-16
I have the same annoying problem... Even by modifying the settings, there are some links that always open in new windows, for instance in livescore.com.
Actually the only thing that freezes is firefox, but really sometimes it makes me want to remove firefox. Any solution to it? I found some lines in about:config about new window but they are integer values, so I don't know if changing them will do any good. Please can somebody help me?

---

### Post by juantovarm on 2006-12-17
I found out what my problem was: Bug 54684. It makes the cpu usage go to 100% and stay there for quite some time making the whole pc unusable. In my case for about 10 seconds. The solutions is very simple: System>administration>softwaresources>internet updates. SELECT ALL. If you do not have these selected yopu won't be able to get the patches necessary to solve this problem. These are:

libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnomevfs2-bin

Hope it helps! :D

---

### Post by janfsd on 2006-12-17
I already had the newest versions of that files, I tried to reinstalled them, but that didn't help. You are right, that problem makes the CPU usage go to 100 %.  That's really strange, other browsers based in  firefox , for instance flock doesn't have this problem. Any other workaround? Could you link me to that bug?

---

### Post by juantovarm on 2006-12-17
Sure, here it is:

[https://launchpad.net/bugs/54684](https://launchpad.net/bugs/54684)

---

### Post by ayoli on 2006-12-17
you may try this. type in FF url bar: 
```
about:config
```
find this key:
```
network.dns.disableIPv6
```
turn it to true, then 
find this key:
```
network.http.pipelining
```
turn it to true.

edit: oops, im offtopic, sunday isn't my best day ;)

---

### Post by janfsd on 2006-12-17
> **juantovarm said:**
> Sure, here it is:

[https://launchpad.net/bugs/54684](https://launchpad.net/bugs/54684)

Thanks, I checked it, but nobody mentions a similar problem there, nothing about opening a new firefox window makes the cpu usage go to 100% ...by the way I am on AMD64.

---

### Post by juantovarm on 2006-12-17
I read in one of these forums that the ubuntu firefox was not as fast as the original one :-k  go figure... why don't you download the firefox from their webpage and install it manually. I did it once while running dapper and it was not difficult at all 

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by bigaltx on 2006-12-17
I've always used Swiftfox [http://getswiftfox.com/](http://getswiftfox.com/) . I installed the deb package because of problems with Firefox not playing video correctly, no video problems since, and it's also faster.

---

### Post by janfsd on 2006-12-17
Yeah, once I tried it, but somehow was crashing often, even like that the ubuntu package is fast on my pc, is just that annoying bug. I always try to open new links in new tabs so I won't get that problem. This thing shouldn't be happening...

---

### Post by janfsd on 2006-12-17
> **bigaltx said:**
> I've always used Swiftfox [http://getswiftfox.com/](http://getswiftfox.com/) . I installed the deb package because of problems with Firefox not playing video correctly, no video problems since, and it's also faster.

Yes, I am looking to try it, but there is one problem, Swiftfox is based on the 32bit build of firefox, and since I am running on AMD64, the plugins I have won't work. I'll have to get all the 32bit plugins.

---

### Post by mrdav1e on 2006-12-22
I followed the System>administration>softwaresources>internet updates. SELECT ALL advice and I followed the about:config, network.dns.disableIPv6 to true, and the network.http.pipelining to true advice and both of these options made a world of difference!
Firefox now works like it should and it is FAST.  Thanks so much!!!
Dave :o)

---

### Post by mrdav1e on 2006-12-22
I followed the System>administration>softwaresources>internet updates. SELECT ALL advice and I followed the about:config, network.dns.disableIPv6 to true, and the network.http.pipelining to true advice and both of these options made a world of difference!
Firefox now works like it should and it is FAST. Thanks so much!!!
Dave )

---

### Post by janfsd on 2006-12-22
Well, I know now what my problem was, because of some extensions i got that problem, I tried create a new profile, and it was fast and did'nt freeze when opening new windows, so maybe i got too many extensions...

---

### Post by l951b951 on 2006-12-31
> **mrdav1e said:**
> I followed the System>administration>softwaresources>internet updates. SELECT ALL advice and I followed the about:config, network.dns.disableIPv6 to true, and the network.http.pipelining to true advice and both of these options made a world of difference!
Firefox now works like it should and it is FAST.  Thanks so much!!!
Dave :o)

I have a fresh install of Dapper Drake (12-28-06).  My Firefox was pokey.  When I clicked on a link, my status bar at the bottom would say looking for "http://****" for about 3-8 seconds before it finally found the website and downloaded the page.  The downloading was fast, but it seemed like it was taking forever to find the website first.  I followed the above changes and now my FIrefox acts like it did under Windows - fast.

---

