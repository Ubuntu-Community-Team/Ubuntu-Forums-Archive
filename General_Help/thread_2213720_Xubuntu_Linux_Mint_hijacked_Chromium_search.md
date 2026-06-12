---
title: "Xubuntu: Linux Mint hijacked Chromium search"
date: 2014-03-28
forum: General Help
---

### Post by green white blue on 2014-03-28
After installing an Xubuntu update today (not sure if this is actually related) I noticed a Linux Mint logo in the upper left corner whenever I searched with Chromium and using its default search engine which is google.com (the options google maps, etc. were gone, very annoying). This is strange since I never used Linux Mint (except for trying it out a year ago for a day) and currently I'm using Xubuntu.

Looking for a solution online it seemed like editing the search engines in Chromium's settings would be a temporary way to fix things. Funny thing is, while I can delete the Mint-related entry, it refuses to accept making my new google.com entry the default search engine. I couldn't edit the Mint-entry either, as the field would turn red and refuse to save its new short url ([www.google.com]("http://www.google.com")). No extension seems to be visibly installed.

First thing I did was to completely delete the google settings as described here: [http://forums.linuxmint.com/viewtopic.php?t=124276&f=6](http://forums.linuxmint.com/viewtopic.php?t=124276&f=6) basically removing my Chromium settings: [COLOR=#2E8B57][FONT=Monaco]sudo rm -fr /etc/skel/.config/chromium ~/.config/chromium
[/FONT][/COLOR]This worked exactly until I synced my Chromium account again.

The solution from here [http://forums.linuxmint.com/viewtopic.php?f=90&t=104823](http://forums.linuxmint.com/viewtopic.php?f=90&t=104823) helped, but now I probably have this thing embedded in my google profile and I don't want that. Will this turn up on my other devices as well? I'm a bit hesitant to try it out. How in the world do the developers justify this behaviour and, more importantly, how do I permanently remove it? Thank you!

---

### Post by Elfy on 2014-03-28
*Thread moved to **General Help**.*

Got a screenshot of this?

---

### Post by robin7 on 2014-03-28
Best guess:  Do you have a separate /data or /home partition that was *not* formatted when you installed Xubuntu?  It may have some left-over settings from that old Mint installation.

---

