---
title: "Channel 4: Ad Blocker Software Alert"
date: 2015-10-12
forum: General Help
---

### Post by jim_deadlock on 2015-10-12
I have  Ubuntu 15.04 + Firefox (v.41) + Pipelight Flash (v.19). Channel 5 on-demand is running like a champ but for some reason channel 4 on-demand is giving this ad blocker alert and refuses to play anything. I do not have any addons installed much less an ad blocker. I've tried a user agent switcher and disabled my firewall but no joy. It's not a website issue because my Windows VM is playing everything fine Anyone else having this issue?

[http://www.channel4.com/](http://www.channel4.com/)

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/adblock.gif[/IMG]

---

### Post by QDR06VV9 on 2015-10-12
I do not get that, But when accepting the Strong Language Warning, Just sets there not loading.
Tried with Firefox and Chromium with no success.

---

### Post by jim_deadlock on 2015-10-12
That's the normal behaviour when you have Linux Flash plugin (v. 11.2), I managed to move past that problem by installing Pipelight Flash, so now this is a new issue.

---

### Post by QDR06VV9 on 2015-10-13
Looks like it will work on Chrome, But I did not create an account to verify.
BTW i have the pipelight enabled, tried with various options.
```
sudo pipelight-plugin --update 
 sudo pipelight-plugin --enable silverlight
 sudo pipelight-plugin --enable flash
 sudo pipelight-plugin --enable wildvine
 sudo pipelight-plugin --enable silverlight
 sudo pipelight-plugin --enable shockwave
```
But Chrome got me to that Login Screen after excepting the warning on strong language.
Just an update Regards

---

### Post by jim_deadlock on 2015-10-13
You need to install hal from ppa:mjblenner/ppa-hal to get the DRM working at all. However, Chrome doesn't work because the Flash plugin uses PPAPI which doesn't have DRM support. This is the kind of mess we are in these days with Flash/Linux :(

---

### Post by coldraven on 2015-10-13
I had so much bother with this, I solved the problem by never watching 4OD again. I hope that they are reading this!

---

### Post by jim_deadlock on 2015-10-14
> **coldraven said:**
> I solved the problem by never watching 4OD again.
I believe this is the correct solution following their "Linux can get stuffed" reply below.
[QUOTE=Channel4]Thank you for your email regarding All 4.

We endeavour to provide the optimal experience of our products across as wide a range of operating systems, browsers and screen resolutions as possible. By necessity, however, full development and testing support is concentrated on those that enjoy the highest levels of usage amongst our users. Linux usage levels are very low and so as an OS does not meet our criteria for full support.

We aim to provide a basic on demand experience across as many operating systems, browsers and screen resolutions as possible, including Linux; however, we are aware that some users running Linux OS are unable to watch on demand content on All 4. We are actively investigating this issue and hope to provide All 4 for Linux users as soon as possible.

We apologise for any inconvenience caused.

Thank you for taking the time to contact All 4.

Kind regards,
 
Andrew Glover
All 4 Support[/QUOTE]

---

### Post by jim_deadlock on 2015-10-27
I have found an actual fix for this. The issue seems to be within the Flash plugin itself rather than anything to do with Ubuntu/Linux.

With flashplugin-installer (Flash 11.2) try any/all of the following:

1. Right-click on a Flash video, go to Settings and disable Hardware Acceleration

2. [Click here]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html") and Reset License Files (you can also get this page via right-click, global settings).

3. Restart browser or reload page a few times (the video sometimes fails to start properly on the first page load for some reason).

I still can't get it working with pipelight flash because it won't load the global settings.

Hope it helps.

---

### Post by tturrisi on 2015-10-28
You could try using a ff extension that lets you change the browser headers that get sent.  Sites detect the browser, browser version, plugins, extensions, version numbers, operating system, resolution, and much more, then load content based on the detected headers.
[https://www.google.com/?complete=0#complete=0&q=firefox+extension+change+headers](https://www.google.com/?complete=0#complete=0&q=firefox+extension+change+headers)

---

### Post by tturrisi on 2015-10-28
Some DRM protected websites may also require you to **install an user agent switcher**, otherwise they will refuse to play the content because your operating system is not supported. You can find a tutorial on how to install one [here]("http://pipelight.net/cms/installation-user-agent.html").
[http://pipelight.net/cms/plugin-flash.html](http://pipelight.net/cms/plugin-flash.html)

---

### Post by jim_deadlock on 2015-10-28
In this particular case (Channel 4) it seems to be an internal Flash issue rather than anything browser-related.

---

