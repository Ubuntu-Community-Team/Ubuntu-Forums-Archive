---
title: "Computer taking ~5 mins. to boot."
date: 2007-12-16
forum: General Help
---

### Post by Fireblend on 2007-12-16
So, for some reason after working fine for about its first week and a half, my computer has decided that its boot sequence is about 5 minutes long. Whenever I turn it on, the bar starts loading, but when it's just about to finish loading, the screen goes black for around 5 minutes, until it decides to show the login screen. The only thing seen in those five minutes is the blinking "_", so nothing is immediately evident.

Any way to get my computer back to its former, quickly-booting self? 

Any help would be greatly appreciated.
Thanks in advance.

---

### Post by ~LoKe on 2007-12-16
```
sudo apt-get install bootchart
```
That'll show you a detailed output of what's happening during the boot process, and how long it's taking.  The logs are image files in /var/log/bootchart (IIRC).

---

### Post by Fireblend on 2007-12-16
Well, it seems to take a shorter amount of time restarting as when I turn it on after being off but the same thing I described earlier continues happening... and 1:30 is still more than it should be, right? it seems to be pretty distributed, although I wouldn't be able to say for sure. Any conclusions from this log?

---

### Post by Fireblend on 2007-12-16
Anyone? I could really use some help here...

---

### Post by Lostincyberspace on 2007-12-16
Have you tried this how to.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It took off about thirty second for me.
It looks like it is hanging on exim4 though, you might try getting rid off it and seeing if that speeds up your time. If you got rid of it it should nock a full minute off the boot time.

Let me know if that does any thing.

---

### Post by ~LoKe on 2007-12-16
Out of curiosity, how important is exim4?  It's a mailer of some sort, but what does it really do?

---

### Post by Lostincyberspace on 2007-12-16
> **~LoKe said:**
> Out of curiosity, how important is exim4?  It's a mailer of some sort, but what does it really do?
Thats exactly what I was wondering. I don't think any thing is worth 1 min of boot time.

---

### Post by Fireblend on 2007-12-17
Woah, eliminating that process seriously sped it up! taking 30 seconds to load now, thanks!

---

### Post by Lostincyberspace on 2007-12-17
Yes boot chart is a good app to use to diagnose boot problems, since it gives a graphical representation of the boot.

---

### Post by ~LoKe on 2007-12-17
Hm...I removed Exim4 as well, no problems, but only got a second boost.  I think I've slimmed it down as much as possible.

---

