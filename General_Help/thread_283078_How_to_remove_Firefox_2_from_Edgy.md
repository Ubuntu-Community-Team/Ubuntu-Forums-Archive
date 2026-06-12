---
title: "How to remove Firefox 2 from Edgy"
date: 2006-10-23
forum: General Help
---

### Post by mn_kthompson on 2006-10-23
I just can't seem to get Firefox2 and Flash to play nice on my edgy box.  I've tried every trick that I can find in these forums.  I've added lines to /usr/bin/firefox
```
xport XLIB_SKIP_ARGV_VISUALS=1
MOZ_DIST_BIN="/usr/lib/mozilla-firefox" MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"
```

I've installed alsa-oss and made changes to /etc/firefox/firefoxrc.

I've tried everything that I can find in the forums, and most of the time it has worked, but with each new update to firefox I have to do all these steps again, and the old tricks stopped working.  I've finally reached the end of my rope, and I'm very annoyed that Internet Explorer is the most reliable browser on my box.

Can I remove firefox2 and go back to the last version of firefox?  Is that safe?  Can I remove firefox entirely and reinstall?
Kevin

---

### Post by ciscosurfer on 2006-10-23
aoss doesn't need to be prepended or modified to get FF2 to work on Edgy.

You can remove it, revert back to an older FF .deb file, or download an older (or newer) version.  Try reinstalling again from the Edgy repos and see if that helps.

Flash 9 needs to be installed in your plugins directory in your FF directory to be used for the specific user wanting it to work...for it to work system-wide, you must install it into the /usr/lib/firefox/plugins/ directory.  Make sure you don't have any instance of FF running (as this has caused problems for people in the past)...start 'er up again and go to flash page that uses Flash 9 to see it in action.  Try cisco.com -- you should a box-dissolve in the upper-right area.

---

