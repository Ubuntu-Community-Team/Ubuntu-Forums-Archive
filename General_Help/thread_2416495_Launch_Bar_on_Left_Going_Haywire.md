---
title: "Launch Bar on Left Going Haywire"
date: 2019-04-10
forum: General Help
---

### Post by johnsmoke on 2019-04-10
This started happening a few weeks ago, my launch bar to the left, it keeps wiggling the icons, even on programs not in use. I can be in any program and to the left it will periodically/randomly display/wiggle an icon, even if it's not in use. For example, the little drive icon would pop up and flash over there even when there's not an external hooked up. Is there any way I can sort of reset the launch bar or something?

---

### Post by johnsmoke on 2019-04-19
No one has any suggestions for this? It's driving me nuts!! If anyone can help, please reply.

In other words, I'm getting wiggling icons in the launcher on things not even in use.

---

### Post by yetimon_64 on 2019-04-19
> **johnsmoke said:**
> No one has any suggestions for this?...
Maybe it would help your thread if you could post what release you are using and what desktop environment is in use. Note: both unity on earlier releases and the newer gnome desktop have a launch bar on the left.

I personally use ubuntu mate most which has no "launch bar" but uses mate panels on the top and bottom. I am familiar with unity and its launch bar on 16.04 as I have an install of it I can boot into, but if you are using a newer gnome desktop release I can't help much as I've never used it. Posting your release version and DE details would be a help here.

---

### Post by QIII on 2019-04-19
> **johnsmoke said:**
> No one has any suggestions for this? It's driving me nuts!! If anyone can help, please reply.

If you do not get a reply to your request within about 12 hours, feel free to bump your request by simply adding a new post with the word "Bump".  That will float your thread up to the top where it is visible.

If you leave a thread for a week, it will sink to the bottom of the ocean to be buried in the ooze where nobody will bother to go looking for it and you won't get a reply.

---

### Post by johnsmoke on 2019-04-24
I'm using Ubuntu 14.04 Trusty and Unity environment

---

### Post by Dennis N on 2019-04-24
Gremlins at work. With an OS very near it's extinction point (5 years support ending), you should instead plan to upgrade very soon to the excellent Ubuntu 18.04.

---

### Post by yetimon_64 on 2019-04-24
> **Dennis N said:**
> Gremlins at work. With an OS very near it's extinction point (5 years support ending), you should instead plan to upgrade very soon to the excellent Ubuntu 18.04.
+1. Trusty at best has less than a week till end of life. Not sure of the exact due date, but assume it is the end on April or about 5 days left at best.

> **johnsmoke said:**
> I'm using Ubuntu 14.04 Trusty and Unity environment
There are a couple of settings in compizconfig-settings-manager (ccsm) you could try setting to "none". That may help stop the icons moving.
See the attached screenshot ...
[ATTACH=CONFIG]283100[/ATTACH]
The screenshot above is from the unity desktop on Trusty 14.04 on this laptop. You are actually lucky that I still have this install active, I was supposed to tarball it and clean out its partitions a couple of weeks ago , but I have been a bit slack :-). Hope the screenshot helps fix the wiggling icons.

Regards, yeti.

---

### Post by johnsmoke on 2019-05-06
I figured this out. Apparently it had nothing to do with Compiz settings, which I tried (remove wiggle etc.), but I had a "loop device" going on. I kept seeing the hard drive icon appear and wiggle constantly on the launch bar. Has something to do with Snapd, this solution worked:

                          "I chased this loop solution to the end of the Internet and found the solution is uninstall **snapd** and **purge all associated** files: (In my case this was 167 Gb)

  [FONT=arial]sudo apt purge snapd"


I got this info from here - [https://stackoverflow.com/questions/5881134/cannot-delete-device-dev-loop0](https://stackoverflow.com/questions/5881134/cannot-delete-device-dev-loop0)
[/FONT]

---

