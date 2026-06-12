---
title: "Flash problems"
date: 2015-07-29
forum: General Help
---

### Post by mlvmhn on 2015-07-29
I have recently installed the Flash plugin in the software center, using the following search: [COLOR=#000000]Adobe Flash Player plugin installer.

It worked fine, however when going to Spotify webinterface, it tells me to "Get Flash". 

What is wrong here? Is the Spotify webinterface broken or something?

The videos in Youtube and other places works fine, but [www.play.spotify.com](www.play.spotify.com) insists to get me to install Flash

I run Ubuntu 14.04 LTS with Chromium. [/COLOR]

---

### Post by howefield on 2015-07-29
What version of flash are you using, seems to be working here with Firefox and flash 11.2.202.491? 

Although given that you use Chromium, you might want to consider pepperflash - the chrome flash player. You shouldn't have to, it's just a suggestion. I use it with Chromium on the basis that it is likely better maintained than the adobe version.

```
sudo apt-get install pepperflash-plugin
```

---

### Post by mlvmhn on 2015-07-29
I got this when running the Terminal command: "Unable to locate package pepperflash-plugin"

What i am doing wrong? (new Linux User)

---

### Post by howefield on 2015-07-29
> **mlvmhn said:**
> What i am doing wrong? (new Linux User)

Nothing, it is me. Apologies, it should be..

```
sudo apt-get install pepperflashplugin-nonfree
```

---

### Post by mlvmhn on 2015-07-29
now it is working, pretty awesome thx :guitar:

---

### Post by howefield on 2015-07-29
Excellent.

Thanks for the update.

---

