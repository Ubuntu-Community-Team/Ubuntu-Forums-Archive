---
title: "Nvidia Beta Driver Issue"
date: 2007-02-18
forum: General Help
---

### Post by BitTorrentBuddha on 2007-02-18
Hi, I had been using nvidia beta for a while, I usually just ignored the upgrade to the kernel, as the repository from which I downloaded the replacement restricted-modules and beta driver had been down for a while. What I want to know now, is how and where from other people have the nvidia beta driver, preferably working with the newest restricted-modules, installed. Any help would be greatly appreciated, thanks.

---

### Post by taurus on 2007-02-18
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by BitTorrentBuddha on 2007-02-22
Sigh*... The problem lies in my horrible ISP not being able to resolve my repositories 9 times out of 10 for some reason. This is a problem I've always had with ubuntu, or any other debian based system. Long story short, my friend downloaded the packages and sent them to me from /var/cache/apt/archives. Thanks for the suggestion though.

---

### Post by majoridiot on 2007-02-22
as a suggestion for the future...

do a nslookup for each of the www addresses in your /etc/apt/sources.list and then replace each
www address with the ip address that comes back.  it would help in the long run.

(you need to be root to edit that source file)

```
sudo gedit /etc/apt/sources.list
```

---

