---
title: "Chromium replaced with hangouts"
date: 2014-04-05
forum: General Help
---

### Post by xentity1x on 2014-04-05
Hi, so I have a bit of a weird problem. I installed google hangouts for chromium, and now ubuntu seems to thing google hangouts is my default browser. When I type in chromium in the dash, it shows the chromium icon but it says hangouts underneat. I uninstalled the hangouts plugin, and now when I click on the icon in the dash nothing happens. I tried reinstalling chromium, but no luck. I can't seem to find the chromium executable anywhere. Anyone know what happened?

---

### Post by bapoumba on 2014-04-05
What does **apt-cache policy chromium-browser** return ?

---

### Post by boss2022003 on 2014-05-22
I'm having the same issue....... This would not be an issue for if it worked properly! Because of this problem, when I click on a hyperlink from another program within Ubuntu it opens up a new Chromium-browser window without opening the link I clicked on. That is my main problem with this issue.
"**apt-cache policy chromium-browser**" returns: chromium-browser:  Installed: 34.0.1847.116-0ubuntu2
  Candidate: 34.0.1847.116-0ubuntu2
  Version table:
 *** 34.0.1847.116-0ubuntu2 0
        500 [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

---

