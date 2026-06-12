---
title: "alsaconf"
date: 2008-02-09
forum: General Help
---

### Post by italys on 2008-02-09
I'm not sure why alsaconf isn't included with the alsa-utils package, but it's really frustrating because I really need it and when I try to compile it by source it reports a missing package (libasound) which I have installed.... I did some research and this problem  is fairly common and pervasive for users who need to configure their soundcard by hand... is there any reason alsaconf is NOT included officially? does it conflict with ubuntu somehow?

thanks,
adam

---

### Post by Sudz on 2008-02-16
For a long story about why it's not you can read here:
[https://bugs.launchpad.net/alsa-utils/+bug/29597](https://bugs.launchpad.net/alsa-utils/+bug/29597)

But a good extract:
> 

Re: "alsaconf is planned for removal from Debian"

Speaking for the Debian ALSA packaging team I'd like to clarify our position. alsaconf is a poorly written and poorly maintained program. Even if it were well written and well maintained, we would prefer to have ALSA packages that worked properly without the administrator have to run a configuration utility every time there is a hardware change. We have almost realized this ideal. However, we continue to get reports that say "Sound doesn't work unless I run alsaconf!". When sound doesn't work unless the user runs alsaconf it means:

* The user's system isn't configured properly. Probably a module name needs to be added to /etc/modules or something.
* The alsaconf utility provided the user with some useful information, even though in an ideal world it wouldn't be needed.

We don't plan to remove alsaconf from Debian soon. However, I am leaning toward changing the program so that it doesn't write out any files, but only prints out debugging information. (The files that it writes out now are superfluous in most cases.) The first thing it will print is "This is a debugging utility. Under normal circumstances you do not need to run alsaconf to configure your system to use ALSA."


---

### Post by hyperair on 2008-02-16
So basically we're seeing that Debian is planning on changing alsaconf into a debugging utility that doesn't mess up your configuration files for you. However, in Ubuntu it's totally missing. Isn't that something?

---

### Post by eyeonthewinner on 2008-05-22
yeah, i hear that, I need alsaconf to get my realtek ac'97 surround sound working. Or at least the easy way that i've done it for a number of years now...

---

