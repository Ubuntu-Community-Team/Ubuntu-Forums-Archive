---
title: "Slow Internet?"
date: 2006-10-14
forum: General Help
---

### Post by xptweakerntn on 2006-10-14
just installed ubuntu! i love it! the only thing is is while somethime the internet is fast, faster than windows could ever think of, sometimes it is slow to react, it takes a while for things to start downloading and sometimes it takes 20 seconds for a page, like google, to load, is there a reason? and is there a fix?

---

### Post by Qrk on 2006-10-14
It might be a firefox bug. Try using epiphany (avialable in the repositories) or Opera (it has an ubuntu .deb available for download in their website)

Firefox's Linux port doesn't seem to get a lot of love from the Mozilla foundation. Switiching to a different browser may be all you need.

---

### Post by xptweakerntn on 2006-10-14
i tried em both. it seems as if when i start up the internet, or a download, it takes a while, but after it does get goin, its alright. but if i wanna switch pages, like from google to yahoo, it takes longer. we have dsl and a router. could the router just not be made for *nix?

---

### Post by adamonduty on 2006-10-14
You might have a search directive in your /etc/resolv.conf file...

If you see any 'search' lines, remove the line, save the file, and then see if you get faster results.

---

### Post by moore.bryan on 2006-10-14
*you might also want to tweak firefox's settings.  there's a ton of different websites to walk you through it... just search for "speed up firefox."  the no-brainer help might be to install the "fasterfox" firefox extension.  also, are you sure the pages are loading slower or do they just feel like they're slow?*

---

### Post by xptweakerntn on 2006-10-14
nameserver 192.168.1.254

that is the only thing in the file.
im not a genius when it comes to linux, but i am pretty sure that i open the right file.

---

### Post by xptweakerntn on 2006-10-14
oh yah, im sure, i tried three different browsers. epiphany, opera, and firefox. google shouldn't take 20 seconds to load, should it?
after it loads, i can search for something, then it appears instantly, i mean instantly! so i don't know. any suggestions?

---

### Post by Bartender on 2006-10-14
Have you tried disabling IPV6?

---

### Post by xptweakerntn on 2006-10-14
what is that? i am new to ubuntu, and linux.

---

### Post by wieman01 on 2006-10-14
> **xptweakerntn said:**
> what is that? i am new to ubuntu, and linux.
To disable ipv6 in Firefox:

> a. URL field: about:config
b. Search for ipv6.
c. Right-click->toggle

To disable "ipv6" globally see this thread (first post): [http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

---

### Post by moore.bryan on 2006-10-15
*also, you might want to check cache size... if it's taking forever to load google, but flying after that, it could be there...*

---

### Post by blackmh on 2006-10-15
It could be that your router is set to dial on demand option in case you have ADSL (pppoe)

---

### Post by CaveRat on 2006-10-15
bump global instructions thread already givin.

---

### Post by adamonduty on 2006-10-16
At the terminal you can also try:

```
time nslookup www.google.com

time ping -c 4 www.yahoo.com

time wget www.slickdeals.net
```

None of those should take more than 2 or 3 seconds to finish, definitely not 20 seconds! These should at least help us narrow down whether the problem is in the network or the browser.

Also, type

```
route
```

and see if it takes more than a second or two to show your default route. Please show us the output of these commands. And another thing - you don't have both wired and wireless connections, do you?

---

