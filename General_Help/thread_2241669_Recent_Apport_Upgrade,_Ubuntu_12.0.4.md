---
title: "Recent Apport Upgrade, Ubuntu 12.0.4"
date: 2014-08-27
forum: General Help
---

### Post by serapis5 on 2014-08-27
Can someone please help?  I just updated hardware support as per the request of update manager.  Rebooted system and all was fine.  Then I had to install 4 new updates 3 of which were about apport and one which I don't recall.  Rebooted, now whenever I open Firefox, instead of an address in the address bar, I get gray blocks.  I can still type an address into the bar, but it will disappear as soon as I hit enter.  I know this is merely a frustration, but it is extremely annoying and if anyone has any assistance they can offer I would greatly appreciate it.

---

### Post by grahammechanical on 2014-08-27
That problem is nothing to do with Apport. Which is a utility that detects system crashes and if we give it permission it will collect log files and then open a link to Launchpad to allow us to post a bug report. Apport is usually disabled on released versions of Ubuntu.

You might want to look somewhere in Firefox settings and see what character encoding is being used. Is it set to Unicode (UTF-8)?

Regards.

---

### Post by serapis5 on 2014-08-27
Changed encoding to unicode from Western, but no luck.  Still have the gray bars in the address bar instead of the actual address of the webpage.  Thanks for yur help anyway.

---

