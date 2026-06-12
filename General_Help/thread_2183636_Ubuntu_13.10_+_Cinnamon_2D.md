---
title: "Ubuntu 13.10 + Cinnamon 2D"
date: 2013-10-25
forum: General Help
---

### Post by Vannyi on 2013-10-25
Just finished installing Ubuntu 13.10 as the only OS on my PC.  After doing the updates, I went into the Software Center, installed Cinnamon 2D, and rebooted.  When I try and sign into the Cinnamon session, I just see a multi-color screen with a mouse arrow and nothing else.

I've also tried reimaging the PC and installing Cinnamon, but have the same issue.

Any thoughts on how to get Ubuntu 13.10 working with Cinnamon?

Thank you

---

### Post by Vannyi on 2013-10-25
Anyone?

---

### Post by deadflowr on 2013-10-25
From what I understand, cinnamon in the repos conflicts with the version of gnome on Ubuntu.
The cinnamon developers over at mint, released cinnamon 2.0 right before Ubuntu 13.10 came out, so I don't think it made it in time for release.

You can install a ppa, though.
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

I'm not sure if it's still accurate, but the one caveat to running cinnamon 2.0 on Ubuntu is it kills unity.
[http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop](http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop)

Of course things change rapidly in Ubuntu and Linux, so this might have been fixed.
Though if you really like cinnamon over unity, then it's probably for your overall liking.;)

---

### Post by Vannyi on 2013-10-26
Thanks for the option to install Cinnamon through an unofficial repository.

However, wouldn't the fact that Cinnamon is available through the Ubuntu Software Center lead one to think that Cannonical has tested and approved its availability for Ubuntu 13.10?  I believe the version in the Software Center is 1.74.  It's available in the Software Center for 13.04, 13.10 but not 12.04.

---

### Post by deadflowr on 2013-10-26
Cinnamon is in universe repository, which are community maintained and not officially supported by Canonical.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Just because a package is in the repos doesn't mean Canonical tests them for every release.(or even can)
There are even completely unmaintained packages in the repos(firestarter?).
Borked packages have been pulled after a new release before.
Myunity is one that comes to mind.

Who knows though.

I did find one bug, similar to yours
[https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1180638](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1180638)

---

### Post by Frogs Hair on 2013-10-26
FYI [http://news.softpedia.com/news/Cinnamon-2-0-Corrupts-Unity-on-Ubuntu-13-10-390736.shtml](http://news.softpedia.com/news/Cinnamon-2-0-Corrupts-Unity-on-Ubuntu-13-10-390736.shtml)

---

