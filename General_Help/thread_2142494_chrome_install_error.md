---
title: "chrome install error"
date: 2013-05-05
forum: General Help
---

### Post by Isaacmarritt on 2013-05-05
hi ubuntu community I recently had a problem trying to install chrome stable onto ubuntu through the terminal came up this  (google-chrome-stable : Depends: libudev0 (>= 147) but it is not installable) has any else had this problem or know the solution

---

### Post by vasa1 on 2013-05-05
[https://code.google.com/p/chromium/issues/detail?id=226002](https://code.google.com/p/chromium/issues/detail?id=226002)

---

### Post by craig10x on 2013-05-05
Get the dependency from the link on step #2 on this article here:
[http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/](http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/)

Select either 32 bit or 64 bit depending on which one you are installing for Chrome....

Then right click the deb file of the dependency and have it open in the Ubuntu Software Center...install it (first)
Then right click your Chrome deb file and open in Ubuntu Software Center...install that

(or you can use the terminal method they outline in the article...either way should work)...

It will successfully install....It's missing a dependency in ubuntu that Chrome is compensating for but won't hit the stable Chrome release for awhile so this is the immediate solution for this problem...

---

### Post by vasa1 on 2013-05-05
> **craig10x said:**
> ... won't hit the stable Chrome release for awhile so this is the immediate solution for this problem...
By my calculations, we should have Chrome 27 stable version this week and I'm waiting for that. (Chrome 26 was released on ~ Mar 26.)

---

### Post by lovebluesky2009 on 2013-05-05
search libudev in the software center&#65292; then install it

---

