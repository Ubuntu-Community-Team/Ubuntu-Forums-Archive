---
title: "Speedtest.net rendering?"
date: 2015-01-15
forum: General Help
---

### Post by d4m1r on 2015-01-15
Hey all, I am having a problem accessing the popular speedtest.net site....This has actually been happening for me across 2 different version of Firefox (my main browser) and Adobe Flash versions. The previous one, and the versions that just recently came out. I was hoping this would go away under Firefox 35 and the latest update to Adobe Flash but it hasn't :( 

As you can tell from my screenshot below, my adblocker is disabled and ALL plugins have been enabled from the top left bar. Even enabled share location by default but made no difference....No matter how many times I restart Firefox, reload the page, or clear my cache, the page **always** loads like this....Practically blank;

[https://i.imgur.com/H5FMMJW.png](https://i.imgur.com/H5FMMJW.png)

---

### Post by CantankRus on 2015-01-16
I don't use firefox but in Trusty the speedtest.net site will load after following this guide 
to install the freshplayerplugin.
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
As stated in the guide, the freshplayerplugin is a wrapper for google-chrome's libpepflashplayer.so
and the easiest way to get libpepflashplayer.so is install google-chrome.

Not sure if you need to uninstall the old Adobe Flash.
I didn't have it installed to start with.

You may want to disable the nilarimogard/webupd8 ppa after installing freshplayerplugin as it
contains possibly unwanted updates to various other packages.
```
glen@Trusty:~$ firefox --version
Mozilla Firefox 35.0
```

---

### Post by sandyd on 2015-01-16
Odd, flashplugin-installer works for me on FF 34.0

---

### Post by d4m1r on 2015-01-16
Thanks for the reply guys but I know about the pepperflash wrapper for Firefox but I DON'T want to use it. Why? Because I'd like 2 different versions of Flash installed to offset situations like this :)

> **sandyd said:**
> Odd, flashplugin-installer works for me on FF 34.0

Have you tried under the new Firefox 35? Any reason you haven't updated yet?

Still trying to figure this out....

Firefox version = **35.0**

Adobe Flash version = **11.2.202.429**

---

### Post by mc4man on 2015-01-16
Just to note speedtest site works fine here with FF35 & flash. Try logging in to a guest session & see if it works  there.

---

### Post by d4m1r on 2015-01-16
Very weird...Restarted my laptop, cleared my cache, disabled ABP, allowed flash + java always, accessing the page again and its working :)

Enabled ABP again and it is still working too.

---

### Post by d4m1r on 2015-02-08
Well, hate to say it but after I recently updated Firefox, Adobe Flash, and Pepperflash, I am having this problem again :(

What's worse? Both under Firefox and Chromium using 2 different versions of Flash....

Firefox = recently released **35.0.1**

Adobe Flash = recently released **11.2.202.442**

Pepperflash = recently released **16.0.0.305 **

I have tried clearing my cache, restarting Firefox and Chromium, rebooting my machine, etc but nothing works and the page always renders like this and just sits there;

[IMG]http://i.imgur.com/DRsTX2J.png[/IMG]


Any ideas on how to fix/troubleshoot this guys? :( Sometimes I hate being on the cutting edge always.....

---

### Post by efflandt on 2015-02-08
Maybe network issues. I have no trouble using [www.speedtest.net](www.speedtest.net) with that firefox/flash version or Google Chrome 40.0.2214.111 (64-bit)/flash 16.0.0.305 (not Chromium in repos) on AT&T DSL (USA).

---

### Post by d4m1r on 2015-02-08
Internet is working fine and other speed test sites also working (getting full speed) so I know it's only a rendering issue for speedtest.net.

Funny enough, their sister site (pingtest.net) renders fine :(

---

