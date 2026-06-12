---
title: "Firefox wont login to an internal site"
date: 2020-09-02
forum: General Help
---

### Post by kingpenguin on 2020-09-02
I have a website that I use for my job all of the time. It is something that allows us to look up old cases to get a better idea on how to support the application that I support. When I use chromium I am able to log in the site no issues at all. I know this will be tricky because I can not just give you access to the site as it is behind my company vpn. I now that when I download the vanilla firefox that this does not have any issues but I want a version of firefox that can be updated with apt get. Something is up with ubuntus version of firefox that is killing this site. I would love to help figure this out. When running a wget -S site it is using ntlm auth.

---

### Post by CelticWarrior on 2020-09-02
The Firefox versions in Ubuntu are the same as in any other OS and updated pretty much at the same time.
It doesn't feel like a problem with a certain version or version though but a problem with some addons, perhaps?

---

### Post by Dennis N on 2020-09-02
If it helps, the Firefox you download from Mozilla web site will update itself automatically provided you make yourself the owner of the Firefox folder and its contents.

---

### Post by kingpenguin on 2020-09-02
CelticWarrior I can tell you that it is a fresh install of firefox that has no addons at all. It just does not handle the ntlm auth correctly. I know this works from the version you can download from the firefox website so I know something is not the same.

---

### Post by ActionParsnip on 2020-09-02
If you use Chrome is it OK there?

---

### Post by TheFu on 2020-09-02
Which release for both firefox and ubuntu?
Recent versions of firefox did ask about using DoH. Perhaps that was allowed and it broke local name resolution? That's just a wild guess.

---

