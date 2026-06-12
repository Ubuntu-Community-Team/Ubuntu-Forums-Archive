---
title: "Upgrading to Firefox 21 causes Firefox to no longer start"
date: 2013-05-19
forum: General Help
---

### Post by thnewguy on 2013-05-19
I'm running Ubuntu 12.04 LTS (64-bit). Yesterday I updated Firefox from version 20 to version 21 using the Ubuntu repositories. Since then trying to launch Firefox produces an error saying my profile cannot be found or is invalid. I tried re-installing Firefox, I tried removing my profile, I tried launching the profile manager. All attempts brought me back to the error saying Firefox could not find my profile and the browser would immediately close.

Eventually I worked around the problem by downgrading Firefox to version 11.0 (available in the Ubuntu repositories). This is a poor work around as it means some add-ons no longer work and all of the security fixes from the past year are not in place. I've tried to report this bug on Lanchpad but the bug reporting tool isn't accepting my report. I thought I'd my problem and work around here in case anyone else runs into the issue. Downgrading Firefox to an old version appears to be the only fix, at least the only one I got to work.

---

### Post by fantab on 2013-05-19
Uninstall FF11.0. Open your Home folder and hit Ctrl+H, and delete .mozilla (dot mozilla).

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get dist-upgrade

Then install FF21.

---

### Post by thnewguy on 2013-05-19
I tried removing the .mozilla directory and doing a complete remove/purge and re-install. It did not correct the problem, Firefox 21 refused to load. It produced the same error saying my profile was missing or invalid. Reverting to Firefox 11 corrected the issue.

An additional piece of info: Once Firefox is working properly again with an older version of the software and with a fresh profile, upgrading to Firefox 21 causes the bug to reoccur. There is a bug report open for this issue on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1181807](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1181807)

---

### Post by fantab on 2013-05-19
Interesting. You should also add to that bug report.

You can download the older version of Firefox from [ftp://ftp.mozilla.org/pub/firefox/releases/20.0.1/](ftp://ftp.mozilla.org/pub/firefox/releases/20.0.1/) then follow [http://www.liberiangeek.net/2012/04/how-to-install-previous-versions-of-firefox-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/how-to-install-previous-versions-of-firefox-in-ubuntu-12-04-precise-pangolin/)

---

