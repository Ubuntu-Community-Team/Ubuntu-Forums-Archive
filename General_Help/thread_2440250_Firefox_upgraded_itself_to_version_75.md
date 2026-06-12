---
title: "Firefox upgraded itself to version 75"
date: 2020-04-07
forum: General Help
---

### Post by tomdkat on 2020-04-07
Hi!  While I was using Firefox 74.0.1 on Ubuntu 19.10 (64-bit), Firefox indicated it encountered a problem and needed to restart.    So, I clicked the button to have it restart.  After a few minutes, I noticed Firefox didn't restart so I started it manually.    I used it for about an hour before I realized the URL bar was different, a little bigger.   So, I looked at the Firefox version and version 75 had been installed!   Firefox 75 was released today (April 7, 2020, I believe) but Ubuntu's software updater didn't do the update (as it usually does).  When I look in the software center, I see two entries for Firefox, one for version 68 (snap) and one for version 74.0.1 (proprietary).   According to the list of snap packages installed, Firefox isn't listed.

So, my question is:  what in the hell happened to enable Firefox to update itself?????

Thanks in advance.  :)

Peace...

---

### Post by deadflowr on 2020-04-08
Probably unattended-upgrades running in the background.
check
```
tail /var/log/unattended-upgrades/unattended-upgrades.log
```
New security update forced a version upgrade to 75.
Firefox on Ubuntu security notices:
[https://usn.ubuntu.com/4323-1/]("https://usn.ubuntu.com/4323-1/")

---

### Post by tomdkat on 2020-04-08
Sounds good.  Thanks for the info!

Peace...

---

