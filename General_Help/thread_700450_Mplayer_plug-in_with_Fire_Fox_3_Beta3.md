---
title: "Mplayer plug-in with Fire Fox 3 Beta3?"
date: 2008-02-18
forum: General Help
---

### Post by mister_k81 on 2008-02-18
So I downloaded the latest beta build of Firefox 3 (3.0~b3) from the repos, and it works great so far... much faster than Firefox 2.0.0.12. But I can't seem to get the mplayer plug in to work with it. Does anybody have any suggestions on what I could do to fix this? Or does the plug in even work at all, at this point?

---

### Post by Redenbacher on 2008-02-18
I'm not able to use many plugins on 3 beta 3. Java and Mplayer being 2 of them, so I think it might be due to the current build.

---

### Post by mister_k81 on 2008-02-18
Ah, you are probably right. I guess I'll just stick to 2.0.0.12 till final release.

---

### Post by puccaso on 2008-02-26
mmm at the moment
im using hardy
and firefox3 is default
and im unable to downgrade.


any suggestions but patience?

---

### Post by mandragor on 2008-02-28
I think the problem is that mplayer-plugin and other such packages only install plugins to the
"old" firefox's plugin directory. This solved my mplayer-problems:

```
cd /usr/lib/firefox-3.0b3/plugins
sudo ln -s /usr/lib/mozilla/plugins/* .
```

Change the first line to suit the version of Firefox 3 you have. You will have to restart firefox
for mplayer to work.

---

### Post by StFS on 2008-03-25
I could not get the symlinking in /usr/lib/firefox-3.0b4 to work.

Instead I did this the following way:

```

cd ~/.mozilla/firefox/plugins
ln -s /usr/lib/firefox/plugins/* .

```

This of course will only work for a single user but has the benefit of not needing to be repeated if you upgrade to b5 (or rc1 or whatever comes next).

---

### Post by mcgarry83 on 2008-04-25
StFS and mandragor, you guys are awesome! This was driving me nuts but I just did what you both were saying and everything works perfectly. Thanks again!

---

