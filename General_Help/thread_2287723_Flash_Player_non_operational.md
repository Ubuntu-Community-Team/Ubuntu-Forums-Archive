---
title: "Flash Player non operational"
date: 2015-07-21
forum: General Help
---

### Post by george120 on 2015-07-21
Hi - just got new laptop with ubuntu op system 12.04 LTS - I checked on adobe site and have downloaded flash player for mozilla firefox 11.2.202.491 for linux - when I check the addons tab under mozilla - it tells me that the plugin is installed and activated, however if I try and access a site which used flash ( eg gambling sites) - I keep getting an error message which states that expressinstall is not supported by the installed op system. Tried downloading chromium but get same error message - any help to get flash working ? Only other suggestion I received was to ditch ubuntu and install a windows system - might be last resort if cannot get it working .

---

### Post by Vladlenin5000 on 2015-07-21
Hi and welcome.

Indeed, Flash is becoming annoying. The best out of the box solution is Goggle Chrome (not Chromium) which comes with an up to date Flash version but even that has issues with certain websites, DRMed contents, etc.

---

### Post by amoun on 2015-07-21
Hi
I'm having problems with Trusty > Firefox > channel5.com on demand

For george 120 and Vladlenin5000 does [http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10](http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10) help solve the DRM. It did before the latest upgrade for flash and DRM channel 4 still works.

So it looks like only the flash on channel 5 is bad and I can't get google chrome to work at all. For soem reason when I try to install I get Chromium ????

---

### Post by Vladlenin5000 on 2015-07-21
Chrome isn't available in Ubuntu repositories, only the open source Chromium it's based on.

[https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html)
Download the .deb file, double-click opens the Ubuntu Software Center, press install.

---

### Post by amoun on 2015-07-22
Vladlenin5000

Thanks for the chrome advice, I did manage to find similar via [http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/](http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/) which installed OK.

Still a) it seems slower than Firefox, Opera and Chromium, which I have installed and b) as yet still can't get channel5.com UK TV to stream?

Thanks again

---

### Post by Vladlenin5000 on 2015-07-22
It shouldn't work any differently than Chromium given the same circumstances. Chrome asks you to login in Google services before anything else and that syncs your profile, history, bookmarks, add-ons, etc. oh, and (usually Windows) malware.
It's unfair to compare a 'loaded' Chrome with a clean Chromium, clean as never sync'd with a Google account. ;-)
Opera is currently based in Chromium so it shouldn't be much different either.

it should just work for Channel 4 or 5 with 12.04 and the method (PPA) for installing HAL should work for newer releases, it [did]("http://blog.terranux.net/2014/04/how-to-get-4od-to-work-on-ubuntu-14-04-trusty/") until last year.

I'm afraid I won't be of much help with that because I cannot test it, I'm not in UK. I can but it would be illegal, apparently :-\":-\":-\":-\"

---

