---
title: "Firefox Flash Player Not working in Ubuntu"
date: 2015-04-04
forum: General Help
---

### Post by stevet747 on 2015-04-04
I cannot access Farmville2 in Facebook with Firefox ver 28.0.  I have installed the flash player in the software center, but it doesn't work.  I attemped to download the flash player from Adobe.com but it will not download.  I'm getting the error "Unknown channel 'trusty-partner' The channel 'trusty-partner' is not known.  I've checked some of the other posts concerning this issue and have only seen 2 options, download the flash player from the software center or use Google Chrome.  I have Google Chrome and it does work, almost.  It is extremely slow. It's worse than Dial Up.  On my windows machine Google Chrome freezes and skips and is very annoying.  But currently my only choice is Google Chrome.  

Is there a fix for this.

Ubuntu 14.04LTS
OS Type - 64bit

---

### Post by TheFu on 2015-04-05
Adobe dropped support for Flash on Linux a few years ago.
Google has been working with Adobe to keep the version of Flash in Chrome as up-to-date as possible on Linux. There are ways to pull that version of Flash from the Chrome installation and use that under either Chromium or Firefox.  It has a new API - Pepper-something.  I don't think there is a trivial way to get this newer Flash to work under Firefox, but I have seen manual steps for it somewhere. [https://askubuntu.com/questions/562271/can-i-use-chromes-pepper-flash-with-firefox](https://askubuntu.com/questions/562271/can-i-use-chromes-pepper-flash-with-firefox)

---

### Post by Impavidus on 2015-04-05
I think (never tried it myself) that facebook is one of those few sites that need a flash version later than 11.2. So the flash for Linux that you can download from Adobe (don't do that, but use the software centre so you can get automatic security fixes) or install via the software centre won't work. The alternative is using the pepper flash plugin, which runs in Chrome or Chromium. There are also some hacks, allowing the Windows flash player in Firefox via wine or the pepper flash player in Firefox (at least, that's what I read somewhere), but those hacks aren't very reliable.

On a separate note, on Ubuntu 14.04 (or any other supported Ubuntu) you can upgrade via the package manager to Firefox 37. Still running Firefox 28 doesn't sound very secure. Just install your updates.

---

