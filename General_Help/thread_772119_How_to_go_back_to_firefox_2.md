---
title: "How to go back to firefox 2?"
date: 2008-04-28
forum: General Help
---

### Post by K.Morgan on 2008-04-28
Just recently upgraded to Hardy Heron and Firefox 3 is annoying me. It doesn't seem to render fonts correctly on web sites, The text on all pages are way too big and nothing i seem to to will change it, so i was wondering how i go back to the version before, as there was no problems with that one.

Kristian

---

### Post by ppm on 2008-04-28
> **K.Morgan said:**
> Just recently upgraded to Hardy Heron and Firefox 3 is annoying me. It doesn't seem to render fonts correctly on web sites, The text on all pages are way too big and nothing i seem to to will change it, so i was wondering how i go back to the version before, as there was no problems with that one.

Kristian

sudo apt-get install firefox-2

---

### Post by K.Morgan on 2008-04-28
Thanks, reverting back to Firefox 2 hasn't solved the problem though, still have fonts that are too large, so not sure how to resolve it.

Kristian

---

### Post by joeybutterface on 2008-04-28
I had the same problem when I upgraded.

Your DPI will be set incorrectly.

If you search for "firefox large fonts ubuntu 8.04" you should find the solution you need to correct it.

---

### Post by vishzilla on 2008-04-28
In firefox enter about:config in the address bar, filter *layout.css.dpi* and edit the value to 96. See if there is any improvement

---

### Post by K.Morgan on 2008-04-28
Done that with the DPI, nothing changed, still got large fonts.

Kristian

---

### Post by vishzilla on 2008-04-28
Hmm, As per this [thread]("http://ubuntuforums.org/showthread.php?t=706788&highlight=firefox+font+huge") many ppl got it solved.

---

### Post by vishzilla on 2008-04-28
If it doesnt work for you, you can revert back to Firefox 2
```
rm -rf ~/.mozilla/ (backup your bookmarks if any)
sudo apt-get autoremove firefox-3.0 firefox-2+
```

---

### Post by K.Morgan on 2008-04-28
Thanks for the help guys, it does appear o be a bigger problem as it's also effecting Thunderbird.  All text in Thunderbird is 3 times bigger than what it was and adjusting the settings doesn't fix the problem, in the process of migrating all data from Thunderbird to Evolution as that seems to be fine.

Looks like I'm stuck with Firefox at the moment as reverting back to Firefox 2 hasn't solved the problem.

Kristian

---

### Post by Nx WinDex on 2008-04-28
Is there a certain way to get download the plugins for firefox. Some times it tells me i'm missing them and lets me install them from a list. I installed the last one and video's aren't working i don't know how to get the screen again? i tried the knosel but it says flash is in stalled? what do i do? worked fine on 7.10

---

