---
title: "How do I remove softwar that wants to remove gnome-core too?"
date: 2013-02-25
forum: General Help
---

### Post by xeddog on 2013-02-25
Subject says it all really.  I want to remove things like ekiga, empathy, and a couple of other things but they all want to remove gnome-core too.  That sounds like it might be a bad idea.  :-)  So how do I remove all this crud that I don't want?

Thanks,

X

Oh,  I am running 64-bit Ubuntu 12.04 and using gnome-shell

---

### Post by kclark on 2013-02-25
You could let it remove what it wants then after it's done reinstall gome-core with apt-get.  Personally I've never ran into any problems with apt removing what it wants to when removing software, but like I said if you run into problems after it's been removed you can always just apt-get it.

---

### Post by xeddog on 2013-02-25
I have also gone ahead and removed software that wanted to uninstall other things that looked desktop related too.  I haven't had any problems until the last time I tried it and I really buggered up my system badly.  I also suspect that if it does indeed remove gnome-core that a re-install will also most likely cause all of the crud to be re-installed too.  We'll see.

Thanks,

X

---

### Post by jwbrase on 2013-02-25
Gnome-core is just a dummy package that pulls in a number of others as dependencies. It should in general be safe to remove it. However, if you use aptitude (rather than Synaptic/Software Center/etc.) for package management, or if you use Computer Janitor, it will try to remove packages that were installed as dependencies if no program depends on them anymore, which could then, as you said, bugger up your system badly.

---

### Post by cortman on 2013-02-25
> **kclark said:**
> You could let it remove what it wants then after it's done reinstall gome-core with apt-get.  Personally I've never ran into any problems with apt removing what it wants to when removing software, but like I said if you run into problems after it's been removed you can always just apt-get it.

Whoa whoa. Best not to do this IMO.

You can set gnome-core to manually installed (i.e., autoremove won't remove it) by running

```
sudo apt-mark manual gnome-core
```

---

### Post by HermanAB on 2013-02-25
It is hard to unscramble an egg. I learned many years ago not to bother trying to uninstall stuff.  If I find something annoying, I remove it from the menu only.

---

### Post by tartalo on 2013-02-25
> **HermanAB said:**
> It is hard to unscramble an egg. I learned many years ago not to bother trying to uninstall stuff.  If I find something annoying, I remove it from the menu only.

Oh, but by removing things you save hard drive, bandwidth during upgrades, sometimes the OS boots faster or uses a bit less RAM, you might be reducing the attack surface... and more importantly you learn about what's under the hood and how things relate to each other, and you might even discover that your computer is capable of things you didn't know it was.

And yes, sometimes you might break your OS irreparably, specially when it says 'To continue, type the phrase "I am aware that this is a very bad idea":', but often the solution is one "apt-get install *whatever-you-just removed*" away.

How would you learn to fix your computer when you need it, if you never break it when you don't?

---

### Post by nothingspecial on 2013-02-25
> **tartalo said:**
> Oh, but by removing things you save hard drive, bandwidth during upgrades, sometimes the OS boots faster or uses a bit less RAM, you might be reducing the attack surface... and more importantly you learn about what's under the hood and how things relate to each other, and you might even discover that your computer is capable of things you didn't know it was.

And yes, sometimes you might break your OS irreparably, specially when it says 'To continue, type the phrase "I am aware that this is a very bad idea":', but often the solution is one "apt-get install *whatever-you-just removed*" away.

How would you learn to fix your computer when you need it, if you never break it when you don't?

Yeah, but not by removing empathy and ekiga. I'm with HermanAB on this one.

---

