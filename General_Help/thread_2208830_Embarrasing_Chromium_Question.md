---
title: "Embarrasing Chromium Question"
date: 2014-03-02
forum: General Help
---

### Post by islamshahjada4 on 2014-03-02
Hello!
I was bored the other day, and what I did was that I kept resizing chromium, moving it to the side, made it bigger, moved it to the side, made it bigger again, etc.  My aim was to see if there would be a point where the Chromium window could not get any larger.  I did that several times, and then closed  the window without returning it to its normal size.  Now, whenever I try to open Chromium, the icon for it shows that its active, but the actual Chromium window doesn't pop up, so I can't use Chromium.  Here's what the icon looks like: [http://lisa.stuy.edu/~shahjada.islam/icons.png](http://lisa.stuy.edu/~shahjada.islam/icons.png)
As you can see, the arrow next to the Chromium icon is unfilled, its just outlined.
Any ideas on how to get Chromium working again?

Ubuntu 12.04 LTS

---

### Post by deadflowr on 2014-03-02
The unfilled arrow means that it is minimized.
Usually clicking it re-maximizes it, but sometimes not.
That can happen sometimes when the program is stuck.
Perhaps try to kill it
something like this might do the trick
```
killall chromium-browser
```
see if that does anything.

---

### Post by islamshahjada4 on 2014-03-02
Thanks!
The killall command didn't work, but you're right about it being minimized.  I maximized it, and it works fine now :)

---

### Post by deadflowr on 2014-03-02
Well, that works.
I was guessing as to what the chromium launcher command is.

But no matter, issue fixed anyway.

---

