---
title: "flash plugin not up to date?"
date: 2013-08-09
forum: General Help
---

### Post by monkblah on 2013-08-09
Hi, I'm using kubuntu 13.04.  I have firefox and ubuntu-resticted-extras installed via the package manager. I also have the package flashplugin-installer installed. I have muon installed which regularly updates my packages.

In firefox, I went to [https://www.mozilla.org/en-US/plugincheck/](https://www.mozilla.org/en-US/plugincheck/) . It reports that my shockwave/flash plugin is not up to date and is vulnerable.

-----------------------
Outdated Plugins Plugin 	Status 	Action
Shockwave FlashShockwave Flash 11.2 r202	vulnerable	Update Now
-----------------------

Shouldn't my system be being kept automatically up to date? What's going on?

---

### Post by SweetAurora on 2013-08-09
Unfortuantly Adobe abandoned Flash for Linux a short while ago and is no longer updated. Fixes and security patches occasionally come out, but no new features or upgrades. The last version for Linux was 11.2. To get an updated copy of Flash, you will have to install Google Chrome as they currently have the rights to develop for flash and regularly update it in Chrome under the name "Pepper Flash".

---

### Post by RadicaX on 2013-08-09
> **kitsuneinari78 said:**
> Unfortuantly Adobe abandoned Flash for Linux a short while ago and is no longer updated. Fixes and security patches occasionally come out, but no new features or upgrades. The last version for Linux was 11.2. To get an updated copy of Flash, you will have to install Google Chrome as they currently have the rights to develop for flash and regularly update it in Chrome under the name "Pepper Flash".

Beat me to it. Sadly Google Chrome is the only way to go for flash right now on Linux, Firefox is working on something about it, an alternative, but till shumway <<<< or whatever it is called comes out, you are stuck with the older flash. Sorry about that.

---

### Post by pqwoerituytrueiwoq on 2013-08-09
shumway dev builds are available here, i don't think it has flv support yet
[https://github.com/mozilla/shumway](https://github.com/mozilla/shumway)

---

### Post by monkblah on 2013-08-10
What is concerning is that the current version is apparently considered 'vulnerable.' Does Adobe really intend to leave millions of linux users of flash open to attack?

---

### Post by SweetAurora on 2013-08-10
No, they release security patches for 11.2 on linux, they just refuse to update it. The "Vulnerable" message I believe is just a generic message saying "Not Version 11.8"

---

### Post by monkblah on 2013-08-10
I see. I think I'm going to install the flashblock plugin on firefox and only run flash on sites I think are safe, just to be sure.

It's a pain in the ass, but flash has been a plague to the open internet for years. I hope it gets supplanted soon by HTML5 or other open technologies.

---

### Post by monkeybrain20122 on 2013-08-10
> **monkblah said:**
> What is concerning is that the current version is apparently considered 'vulnerable.' Does Adobe really intend to leave millions of linux users of flash open to attack?

Never mind that, I think that warning is for Windows because in that platform outdated flash doesn't get security updates. While there is no new feature updates for flash in Linux (unless you use Chrome) I have been getting regular security updates, that page also says mplayer-plugin is outdated, I don't think it even makes any sense (it is normally frozen if you install from the repo)

---

### Post by RadicaX on 2013-08-10
Yeah, Adobe throws fits sometimes, they do not care much for Linux, so any little thing to cause a problem, seems they do it.

---

### Post by Rebelli0us on 2013-08-10
What about Chromium? It has the same version Flash as my Firefox?

---

### Post by RadicaX on 2013-08-10
> **Rebelli0us said:**
> What about Chromium? It has the same version Flash as my Firefox?

As far as I know that is correct, but I have heard of some people tweaking it to run the same kind of flash as Chrome. You might do a yahoo search for that or look on the forums.

---

### Post by kurt18947 on 2013-08-10
> **Rebelli0us said:**
> What about Chromium? It has the same version Flash as my Firefox?

AFAIK, Chromium is the same.  I did find reference to a ppa to install PepperFlash (or whatever it's called) in Chromium.  I bookmarked it but haven't tried installing it, the version in the repositories works fine for me.  Here's the link, use at your own risk:

[https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash)

---

