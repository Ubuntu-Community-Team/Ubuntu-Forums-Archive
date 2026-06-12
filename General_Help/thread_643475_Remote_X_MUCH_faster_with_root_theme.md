---
title: "Remote X MUCH faster with root theme"
date: 2007-12-17
forum: General Help
---

### Post by superyounan1 on 2007-12-17
A few weeks ago I followed instructions on another thread to make my root theme the same as my user theme, i did the following:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

It worked nicely, but I noticed a side-effect: prior to this, applications launched with Remove X invocation were not themed, or in other words they just used the ugly root theme, but I didn't mind it. Now they are however, and it has made remote X unusably slow. 

I removed the symbolic links that altered my root's theme, but remote applications haven't reverted back to the faster theme-less versions.

I can verify the speed difference by running applications as root or as the user remotely, and I'm sure the theme is the problem.

How can i set it back?

---

### Post by superyounan1 on 2007-12-19
bump-itty-bump

---

