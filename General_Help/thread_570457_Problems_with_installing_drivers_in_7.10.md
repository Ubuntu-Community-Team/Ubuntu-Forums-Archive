---
title: "Problems with installing drivers in 7.10"
date: 2007-10-08
forum: General Help
---

### Post by revolve on 2007-10-08
I've used Ubuntu before, back when it was 5.10, and then I migrated back to XP for a while. However, I got a slightly used laptop, and decided to throw Linux on that. I downloaded 7.10 and installed it, and it installed okay(Had some trouble installing it right, but it's working now). However, I want to install the driver for my wifi card(Broadcom), and Adept says that it can install it(It's a restricted driver), but whenever I try to install it, it says "Error committing packages", or something along those lines.

It also says that whenever I try to install anything via Adept.

---

### Post by orbish on 2007-10-08
unfamiliar with adept, my idea would be to jump into the terminal and report back what it reports as the problem... more detailed information for us

sudo apt-get install (package name)
enter your password

not to get too ahead of you, i've heard many times that you need to use ndiswrapper in order to get wireless devices working correctly... report back the error because it sounds like a problem with the package manager as a whole

---

### Post by strabes on 2007-10-08
Check [this page](http://www.google.com/bookmarks/url?url=https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff&zx=K-LwqNhse2k&ct=b) for info about installing broadcom cards. If you follow the instructions exactly it should work.

---

### Post by Naatan on 2007-10-08
are you installing it using the terminal / synaptic or the restricted driver management?

---

### Post by revolve on 2007-10-08
> **Naatan said:**
> are you installing it using the terminal / synaptic or the restricted driver management?

restricted-driver management.

---

### Post by Naatan on 2007-10-08
Have you updated your Ubuntu completely? 

It would help if you would give us the exact error message.

---

### Post by revolve on 2007-10-08
> **Naatan said:**
> Have you updated your Ubuntu completely? 

It would help if you would give us the exact error message.

Here's the error message I get using regular ubuntu 7.10:

"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"

although that was probably because i tried running it while doing an upgrade of my system

---

