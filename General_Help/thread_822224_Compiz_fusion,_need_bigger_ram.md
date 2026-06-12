---
title: "Compiz fusion, need bigger ram?"
date: 2008-06-08
forum: General Help
---

### Post by enoughsaid05 on 2008-06-08
Hi all, just a question.

I have this 512mb of ram and AMD64 2.0Ghz processor. When I switched on Compiz Fusion, everything seems fine, but when I fire up Firefox, Thunderbird and Pidgin, everything seems to be extremely slow. The window will freeze for some time, then it will fade and tell me that the application is not responding. I am thinking of whether to upgrade my RAM or not. Any advice? Should I upgrade my RAM? Does upgrading my RAM will do any help to make the desktop run smoother?

And one thing that I notice, the RAM will hit 84% usage with around 30% swap space used. Is this a good sign?

Thanks in advance!

---

### Post by wdaniels on 2008-06-08
> **enoughsaid05 said:**
> Does upgrading my RAM will do any help to make the desktop run smoother?

Certainly. I find that increasing RAM up to about 2GB is still helpful for 'typical' desktop performance - after that it probably won't make so much difference unless you do a lot of things, such as video editing, that use lots of RAM.

Another big factor with things like compiz is the graphics card, which is usually more expensive to upgrade than RAM, and probably, with only 512MB RAM it's not likely the video card that's the bottleneck. But if you think the video card is struggling then just tune down some of the effects.

There is a good program called CCSM (CompizConfig Settings Manager) that you can install for fiddling with the compiz settings:

```
sudo apt-get install compizconfig-settings-manager
```

> **enoughsaid05 said:**
> And one thing that I notice, the RAM will hit 84% usage with around 30% swap space used. Is this a good sign?

It can be difficult to assess the RAM usage in Linux because it will always use any 'spare' RAM for caching, and will also tend to swap inactive RAM pages out to disk even before you actually run out of RAM (if it thinks that you will get better performance from using the inactive RAM for caching instead). You can adjust the tendency to do this with a variable called "swappiness", which is 60 by default, and you might want to experiment with some lower values, e.g.

```
sudo sysctl -w vm.swappiness=20
```

...or even some higher values if you tend to keep a lot of stuff open in the background when you're not using it. But in most cases, to gain *smoother* rather than *higher* performance you would want to avoid swapping until it's actually needed (i.e. lower values).

One thing I strongly suggest you do to save RAM, is look through the list of services that are automatically started, and disable any that you don't need to be running all the time.

---

### Post by enoughsaid05 on 2008-06-08
Wow! Thanks for the info!

---

