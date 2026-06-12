---
title: "Insane  Processor Usage"
date: 2008-05-02
forum: General Help
---

### Post by Phantom784 on 2008-05-02
I'm running Hardy on my new laptop (2.5ghz dual core, 3 gig ram).  For some reason, even with no programs urning on a blank desktop, the processor usage jumps up near 100% on one of the cores, and it keeps swapping  back and forth.  This makes the computer noticeably slow,  especially when using firefox.  I also have hardy on my older, slower desktop  system,  and this problem doesn't exist there.

---

### Post by olejorgen on 2008-05-02
```

top

```

---

### Post by pjkoczan on 2008-05-02
Check out what processes are taking up so many cycles. You can either check the "Processes" tab, or run "top" in the terminal if you so choose. You can then choose to end or kill the process. If you're unsure what the process is doing, you should ask someone before killing it.

It could be that you have some previous process that didn't end properly. I've seen this sometimes with media players.

---

### Post by Phantom784 on 2008-05-02
nothing in top is listed as using more than 1%

---

### Post by yaknowwat on 2008-05-02
The Problem is the system monitor itself it drains an insane amount of power on some CPU's

I suggest changing the resources update Interval to at least 1 second.

Edit > Preferences |> Resources

---

### Post by olejorgen on 2008-05-02
But top does not. You noticed these spikes in the "cpu applet"?

Be sure to stare at top for a couple seconds, since it might be that it's periodic short bursts from a process. It should show up in top

---

### Post by Phantom784 on 2008-05-04
After watching "top" for a bit, I noticed that Xorg and firefox are the heavy processer users.  I installed swiftfox but it seams to use just as much processor speed as firefox.

---

### Post by redactech on 2008-05-05
Web pages that have flash content seems to trigger that kind of cpu usage. It's annoying but it's flash.

---

