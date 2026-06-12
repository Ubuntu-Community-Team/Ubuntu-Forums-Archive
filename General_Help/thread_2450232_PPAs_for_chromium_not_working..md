---
title: "PPAs for chromium not working."
date: 2020-09-09
forum: General Help
---

### Post by ajgreeny on 2020-09-09
For a long time, ie since installing Xubuntu Focal, I have been using the PPAs from either [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) or [http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu).

They have been working wonderfully with no problems.
However today when upgrading my system I am not seeing any packages mentioned from either of those PPAs, but neither am I getting any error from the update ot upgrade command telling me the PPA no longer exists and the current version 86 from the PPA will "upgrade" to 85, but now as a snap.

I have searched for info about these two PPAs but can find no information.
Does anyone else know what's going on?

---

### Post by TheFu on 2020-09-09
Sorry, no.
Looks like a new chromium was pushed out since Saturday. Perhaps the PPA team just hasn't had time yet?

But have you considered switching to a different chromium-based browser like Brave?  I'm not using 20.04 on my desktops yet - still using 16.04, so chromium is still a normal package there.

```
$ dpkg -l |grep chromium-b
ii  chromium-browser     **84.0.4147.105-0ubuntu0.16.04.1**     amd64  Chromium web browser, open-source version of Chrome
```

And on 20.04 - snap ... 
```
$ snap list
Name               Version                     Rev   Tracking       Publisher   Notes
chromium           **85.0.4183.102**               1298  latest/stable  canonical&#10003;  -
```

BTW, there was a way to run the chromium snap outside the snap container, if you needen that.
```
$ more ~/bin/chromium.sh 
#!/bin/bash

/snap/chromium/current/usr/lib/chromium-browser/chrome &
```
Yep, that still works, but firejail cannot be used with it. ;(

---

### Post by ajgreeny on 2020-09-10
Thanks TheFu.

I messaged the PPA developer/owner Saikrishna Arcot, last night and was told the version scheme that Ubuntu uses in 20.04 has changed, meaning that version 85, for the moment, takes precedence over version 86 provided by the PPA I use; strange what numbers can mean in different situations!

Anyway, plans are in place to update the PPAs quickly to make sure that the versioning again means that the PPA versions will take precedence over the repo version, which, of course, is the snap.

I do see the reasoning behind snaps being introduced but I do not personally think it was appropriate to do so in an LTS version without offering an option to not use them, and to go back to using .deb packages, if that is what users preferred.

---

### Post by CelticWarrior on 2020-09-10
I have nothing against snaps, I use snaps.

I was using chromium-dev not because it's not a snap but because it has the experimental hardware acceleration, something sort of needed for low end Celerons and 60fps Youtube videos.
Now I'm not sure that even if (and when) the PPA is "fixed" I can get the dev branch back.

---

### Post by VMC on 2020-09-10
I don't use snaps at all. I have been using Chrome, but notice a lot more junk now. Just installed Brave [Version 1.16.7 Chromium: 85.0.4183.102 (Official Build) nightly (64-bit)]("https://brave.com/latest/"), it has a built in ad blocker. I normally use ublock, but Braves seems to be on par with ublock.

The Brave is just a deb file, so easily installed without snaps.

---

### Post by CelticWarrior on 2020-09-10
"Problem" solved with a new update. Snap version uninstalled, everything back to what it was.

Amazing how fast things move when highly respected people from here contact the right people.

---

### Post by ajgreeny on 2020-09-11
Great news!

I have messaged the PPA owner again giving thanks for this speedy update.

---

