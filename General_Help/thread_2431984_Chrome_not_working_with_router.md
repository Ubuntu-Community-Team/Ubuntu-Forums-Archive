---
title: "Chrome not working with router"
date: 2019-11-25
forum: General Help
---

### Post by u666sa on 2019-11-25
Firstly let me say that I'm not having this same issue in Windows 7 with chrome, only on linux. Also browser Chromium and Firefox does not do this. Check this strange situation out.

I have Keenetic 1, ip is 172.16.3.1.. Old router. I tried different firmwares on it, first openwrt and then native NDMS. 
Well guess what, Chrome, somehow memorized that my router had openwrt, and it throws me into 172.16.3.1/cgi-bin/luci
but I have NDMS on it, and that address gives me 404 Not found.. Like this in the picture.

[URL="https://imgur.com/YX7wG8D.png"]
  [IMG]https://imgur.com/YX7wG8Dl.png[/IMG][/URL]


now check this out, I open up Chromium or Firefox and type in same address


[URL="https://imgur.com/oDk4TjI.png"]
  [IMG]https://imgur.com/oDk4TjIl.png[/IMG][/URL]


Thus far I have tried going to Chrome history, locating all entries with 172.16.3.1 and deleting them.. This does not help.

I also tried signing off from my synchronization account and deleting all history. This does help. But only temporarily. If I go ahead and install openwrt again on the router same thing happens. I again have to clear all history. Besides, I need my synchronization account for all passwords and usernames and stuff.. So this solution is crap..

Please help. This bothers me.

As I said before, this kind of thing does not happen under Windows 7.

---

### Post by aljames2 on 2019-11-25
I do not use chrome, but it&#8217;s likely something simple.  When you clear the browser cache it should not delete your passwords and form data unless you have it configured to do that.  All browsers are granularly configurable in what exactly you wanted to delete when clearing.  Next, you said that it worked after you cleared the browser history, but then when you change the firmware again it stopped working...this makes sense, because the browser is simply recalling the last version of that IP address page from cache.  You would need to clear the browser cache again in order for the new version of that webpage to refresh.  Another thing, When you enter an IP address in the address bar get in the habit of entering the proper address format such as:  [https://192.168.xx.x]("https://192.168.10.1:44614"):44125 (including any non-standard port numbers, if any are in use, after the colon).

---

