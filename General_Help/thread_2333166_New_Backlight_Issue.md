---
title: "New Backlight Issue"
date: 2016-08-07
forum: General Help
---

### Post by sccjono on 2016-08-07
Hello all,

I have titled this as "new" as it has only developed as an issue since a recent update. I am using 16.04, and have been since it was released, on a HP Pavilion G6 laptop. From previous versions of Ubuntu I have added a line to my rc.local file that reads "echo 255 > /sys/class/backlight/radeon_bl0/brightness" which has always kept my preference of having my screen kept at its brightest setting. But for the lat two days my screen seems to be defaulting to its darkest setting. This is so dark it looks like the laptop is turned off. After a reboot all is fine until I log in to Unity...It goes dark. If I unplug the mains lead...It goes dark. I plug the lead back in...It goes dark. Of course I can turn the brightness back up but its very frustrating.

Any ideas?

jono

---

### Post by &amp;KyT$0P# on 2016-08-07
What does this command show?
```
cat /sys/class/backlight/radeon_bl0/max_brightness
```

---

### Post by sccjono on 2016-08-08
255. Like I said all worked perfectly until recently. It is like a bug or that somehow the system was default the brightness value to 0.

jono

---

### Post by sccjono on 2016-08-11
bump

---

### Post by sccjono on 2016-08-11
I spoke too soon. It look as though it was a bug as an update to LightDM this morning seems to have resolved the issue and all now works as it did before.

Thanks,

jono

---

