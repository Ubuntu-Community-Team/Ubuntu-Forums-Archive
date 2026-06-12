---
title: "Get flash to work in chromium 62?"
date: 2017-11-15
forum: General Help
---

### Post by Jan_Johansson on 2017-11-15
Anyone have it working and know how to help me with this?

Peach OSI (Xubuntu 32bit)

I tried so many suggestions on the net that my head is spinning, but it would seem I'm not the only one

[https://forums.adobe.com/thread/2298071](https://forums.adobe.com/thread/2298071)

Can someone help me or is it a lost cause?

JBJ

---

### Post by Dennis N on 2017-11-15
Starting with Chromium 62, you need to authorize flash on each web site, or web page: 

Two ways

1) I did this:

Settings > Advanced > Privacy and Security > Content Settings > Flash > Allow > Click on ADD, and paste the the URL of the page on which you want to allow flash. You can also use a wildcard symbol to enable the entire site. 

2) I'm now aware you can also do the following, but it sounds like this method affects the entire web site (haven't tested it yet):

Click on the site information symbol at the left end of the address bar. Go to "Flash" and select "Always allow on this site"

In either case, the "Always Ask" choice seems not to work.

---

### Post by Jan_Johansson on 2017-11-16
Hi, I already did all the suggested and everything on this site [https://helpx.adobe.com/dk/flash-player.html](https://helpx.adobe.com/dk/flash-player.html) and this one [https://support.google.com/chrome/answer/6258784](https://support.google.com/chrome/answer/6258784) I also tried all the suggested(there is alot) places to put the libpepflashplayer.so - anyways I still can't get the above page to see flash as enabled and in the bottom of the page, the animation will not play.

Can you tell me where your libpepflashplayer.so is located?

---

### Post by Dennis N on 2017-11-16
> Can you tell me where your libpepflashplayer.so is located? 

Location for flash plugin(s):

```
dmn@Sydney:/usr/lib/adobe-flashplugin$ ls
libflashplayer.so  libpepflashplayer.so  manifest.json

```

Also here:

```
dmn@Sydney:/usr/lib/chromium-browser/PepperFlash$ ls
libpepflashplayer.so  manifest.json
```

---

### Post by Jan_Johansson on 2017-11-18
Thank You, I did not have the PepperFlash folder, so created it and copied 
libpepflashplayer.so and manifest.json

to both PepperFlash and adobe-flashplugin

The [http://isflashinstalled.com/]("http://http://isflashinstalled.com/") claims that flash is not installed. 
[https://helpx.adobe.com/dk/flash-player.html](https://helpx.adobe.com/dk/flash-player.html) says Flash is disabled. If it were not installed then it would say so.

So guess Google disabled it completely in 62.

---

### Post by Dennis N on 2017-11-18
> **Jan_Johansson said:**
> Thank You, I did not have the PepperFlash folder, so created it and copied 
libpepflashplayer.so and manifest.json

to both PepperFlash and adobe-flashplugin

The [http://isflashinstalled.com/]("http://http://isflashinstalled.com/") claims that flash is not installed. 
[https://helpx.adobe.com/dk/flash-player.html](https://helpx.adobe.com/dk/flash-player.html) says Flash is disabled. If it were not installed then it would say so.

So guess Google disabled it completely in 62.

You have to authorize the test page in order for it to detect the flash plugin. On first try, it said no for me as well. After authorizing the page, it was detected. The easy way to authorize is to use method 2 of post #2.

_Update_: I just determined that the PepperFlash folder isn't used in Ubuntu. I deleted the PepperFlash folder and contents, and flash is still detected by the test pages. But that folder is used in some other Linux distros.

---

### Post by monkeybrain20122 on 2017-11-18
> **Jan_Johansson said:**
> Hi, I already did all the suggested and everything on this site [https://helpx.adobe.com/dk/flash-player.html](https://helpx.adobe.com/dk/flash-player.html) and this one [https://support.google.com/chrome/answer/6258784](https://support.google.com/chrome/answer/6258784) I also tried all the suggested(there is alot) places to put the libpepflashplayer.so - anyways I still can't get the above page to see flash as enabled and in the bottom of the page, the animation will not play.

Can you tell me where your libpepflashplayer.so is located?

Instead of going throgh a hoop to get flash working why don't you just use Chrome?? Chromium is a beta and poorly maintained, it is neither here nor there. It kind of doesn't make sense to use Chromim because it is open source and then go through great lenght to get the proprietary stuffs (like flash)in Chrome to work so that all you end up  wth is nothing but an outdated and more buggy Chrome.

In Chrome the default is ask to activitate, but on some sites such as that test site there is no pop up to ask. Instead, click the little cirlce with the i inside in the url bar and choose flash > always allow on this site and reload then you will see flash working.

---

### Post by Dennis N on 2017-11-18
> In Chrome the default is ask to activitate, but on some sites such as that test site there is no pop up to ask. Instead, click the little cirlce with the i inside in the url bar and choose flash > always allow on this site and reload then you will see flash working. 

Chromium works exactly the same way and has the same options with the site information menu (the little circle with the i inside). That was method 2 of post 2. Thing is, the "always ask" does not seem to be working - the "Always allow on this site" does.

---

