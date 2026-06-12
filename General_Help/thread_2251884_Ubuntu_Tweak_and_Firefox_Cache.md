---
title: "Ubuntu Tweak and Firefox Cache"
date: 2014-11-07
forum: General Help
---

### Post by mountainman70 on 2014-11-07
I am running Ubuntu 14.04 LTS with Mate Desktop. Firefox 33.0
I can use Ubuntu Tweak 0.8.8~1~trusty1 and clean everything except Firefox cache .
It shows three things to clean:
startupCache 1.1mb
thumbnails 309.2 kb
cache2 4.0 kb

It just shows a spinning wheel but does nothing.
How do I fix this?

---

### Post by vasa1 on 2014-11-07
My preference is to use the program that generates those files to remove them. Pressing ctrl+shift+delete gives you a screen to clean up from within Firefox itself.

By the way, I also made a change from within about:config to stop Firefox from generating thumbnails at all (because I don't rely on the New Tab page). I made a new `about:config` entry of type `boolean` called `browser.pagethumbnails.capturing_disabled` and set it to `true`.

---

### Post by mountainman70 on 2014-11-07
> **vasa1 said:**
> My preference is to use the program that generates those files to remove them. Pressing ctrl+shift+delete gives you a screen to clean up from within Firefox itself.

By the way, I also made a change from within about:config to stop Firefox from generating thumbnails at all (because I don't rely on the New Tab page). I made a new `about:config` entry of type `boolean` called `browser.pagethumbnails.capturing_disabled` and set it to `true`.

Thanks for replying.

Pressing ctrl+shift+delete in Firefox does not give me a screen.

---

