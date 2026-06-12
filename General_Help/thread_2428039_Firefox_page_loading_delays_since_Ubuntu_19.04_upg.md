---
title: "Firefox page loading delays since Ubuntu 19.04 upgrade"
date: 2019-09-29
forum: General Help
---

### Post by dkarnows on 2019-09-29
Since upgrading to Ubuntu 19.04 (now a few months back) I've been having Firefox issues. When I first launch the pages take a long time to start loading (say two minutes). It's not a network issue because I can launch Chrome and get the pages immediately*. Once those first pages come back it works fine mostly, immediate responses for loading new pages, except after some time video in the browser (say Youtube) starts performing badly, again going to a new video seems to hang in a buffering-type state (although again, I don't think its a network lag issue) for a minute or so before it starts playing.

I don't know if my issue is Ubuntu or Firefox or related to my hardware (running on a Macbook Pro, which I know is not that common).

Any ideas?

Ubuntu: 19.04
Firefox: 69.0.1
Desktop environment: Xubuntu (xfce) but I have the same issue when I try Gnome.
Hardware: Macbook Pro

*  I've seen some similar although less pronounced problems with Chrome but I don't use it much so I have a less comprehensive understanding of the issues there.

---

### Post by uRock on 2019-09-29
The first thing I would try would be closing Firefox, then renaming the .mozilla folder in the Home directory, then reopening Firefox. If this fixes things, then you can rename the old .mozilla back to its original and export passwords and favorites, then import them on the new profile.

---

### Post by dkarnows on 2019-10-04
This worked! You rock urock :-)

---

### Post by uRock on 2019-10-04
I'm glad that worked out for ya!

---

