---
title: "Lubuntu 14.04 Firefox crashes randomly"
date: 2014-07-28
forum: General Help
---

### Post by Chrisfs on 2014-07-28
Hi, 
I upgraded from Ubuntu 12.04 to Lubuntu 14.04. Since then Firefox, which never crashed, has crashed sporadically. Most often it crashes and give the 'problem report' dialong just after I have closed it. However it has also just seemingly crashes arbitrarily while I was clicking in arbitrary places on a web page,

---

### Post by bapoumba on 2014-07-28
That wont help you much, but I am not experimenting Firefox crashes here.
Which version are you running ?
```
apt-cache policy firefox
firefox:
  Installed: 31.0+build1-0ubuntu0.14.04.1
  Candidate: 31.0+build1-0ubuntu0.14.04.1
```
Anything from the terminal if you run firefox from there (other than a GLib warning) ?

---

### Post by qwerkus on 2014-07-28
Hi, I had a similar problem; it turned out to be flash related. Updated the flash-plugin, and now it seems to run smoother.

---

### Post by Chrisfs on 2014-07-28
Looks like the same. 
firefox:
  Installed: 31.0+build1-0ubuntu0.14.04.1
  Candidate: 31.0+build1-0ubuntu0.14.04.1
  Version table:
 *** 31.0+build1-0ubuntu0.14.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
        100 /var/lib/dpkg/status
     28.0+build2-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages

---

### Post by vasa1 on 2014-07-28
> **Chrisfs said:**
> Hi, 
I upgraded from Ubuntu 12.04 to Lubuntu 14.04. Since then Firefox, which never crashed, has crashed sporadically. Most often it crashes and give the 'problem report' dialong just after I have closed it. However it has also just seemingly crashes arbitrarily while I was clicking in arbitrary places on a web page,
Do you regularly do a "cross" upgrade? Your previous OS was Ubuntu. Your current is Lubuntu. 

Maybe the Firefox crashes are not related to the "upgrade" but to a corruption of your profile? Have you run the standard diagnostic steps such as trying a new profile, or running in safe mode (in case an extension has decided to misbehave)?

Is there any correlation between the web page and the crashes? If it's a specific webpage, sharing that page's link may help others test.

Are you running short of RAM? What are your hardware specs?

If you provide more information, it may be easier for someone to help you.

support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles
support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode

---

### Post by Chrisfs on 2014-08-16
Hello, 
I am sorry for not replying sooner. Yes I did cross upgrade from Ubuntu to Lubuntu . I have reset my profile and that does not help. I ran for a while with no add ons but Firebug and that did not help either (nut not in actual Safe mode).
It seems to happen most often when I close Firefox and when I am on a page that auto-refreshes. For example, I will go to plus.google.com and it will show the page and then loading more recent posts, when it refreshes the page to display the more recent posts, I often get a crash as well.  Here is a url for one of those G+ crashes. [https://crash-stats.mozilla.com/report/index/12ed20fd-26da-49b4-9f93-b7b472140816](https://crash-stats.mozilla.com/report/index/12ed20fd-26da-49b4-9f93-b7b472140816)
It happens elsewhere as well, but this is fairly reliable.

---

