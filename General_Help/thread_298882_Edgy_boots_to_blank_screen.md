---
title: "Edgy boots to blank screen"
date: 2006-11-13
forum: General Help
---

### Post by paulgb on 2006-11-13
I did a fresh install of Edgy with no problems, and when I restarted the computer for the first time, it worked fine. After the next restart, though, I could not boot back into X. The mouse would appear briefly (along with a small horizontal bar of apparently random pixels at the bottom of the screen), but then it would disappear and the screen would go blank.

I tried another install and had the same problem. I can boot into recovery mode, but 'startx' causes the blank screen issue.

The computer has an integrated Intel Extreme chip with 64MB of video memory.

---

### Post by taurus on 2006-11-13
Sounds like you need to reconfigure your X again.  Boot into recovery mode and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```
And when you're done, type "startx" to see if X comes up again.

---

### Post by paulgb on 2006-11-13
> **taurus said:**
> Sounds like you need to reconfigure your X again.  Boot into recovery mode and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```
And when you're done, type "startx" to see if X comes up again.

Thanks, this seems to be working. Although I had to guess at all the settings, and the resolution/refresh rate settings I chose seem to have no effect on the actual resolution and refresh rate. Going into "Preferences->Screen Resolution" doesn't fix the problem because the options aren't there. But at least it's working, thanks again.

---

