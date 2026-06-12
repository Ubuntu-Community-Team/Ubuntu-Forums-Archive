---
title: "Chrome opens maximized (usually)"
date: 2022-02-08
forum: General Help
---

### Post by marcw on 2022-02-08
In the past week or two my Chrome started behaving oddly.  It tends to open maximized.  Sometimes it will open a bit smaller but never where it was when it closed and usually maximized.  It never used to do this.  It's easy enough to resize but it's starting to drive me bonkers.  No other changes to the computer except for updates.  Running 20.04.  Any ideas?

---

### Post by uninvolved on 2022-02-08
I didn't want to tamper with my Chrome, so I used Opera. It's too late in the day to go opening VMs and playing around. So, here's a possible hint for you to get what you're after.

I used this to open Opera (which opens full screen by default):

```
opera --window-size=800,600 https://www.google.com
```

The first time I opened it that way, I had to make the window smaller by clicking the resize window. I then closed Opera and reopened it, where it then opened at the screen size I dictated.

That was in the terminal. 

If you play around by editing the Google Chrome application shortcut, appending the window size to the command, it *may* do the trick for you. You shouldn't need to specify the URL like I did.

---

