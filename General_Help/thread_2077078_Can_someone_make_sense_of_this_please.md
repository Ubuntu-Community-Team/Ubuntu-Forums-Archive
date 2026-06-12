---
title: "Can someone make sense of this please"
date: 2012-10-27
forum: General Help
---

### Post by Jcpayne on 2012-10-27
I'd like to know what these "events" are:

```
computer@Computer-PC:/dev/input$ ls
by-id    event0  event2  event4  event6  event8  mice
by-path  event1  event3  event5  event7  event9  mouse0
```

I'm looking for my keyboard input, and I believe one of these is... How do I find out what these different events are?

And for that matter, what are events?

Thanks
jc

---

### Post by Jcpayne on 2012-10-27
I certainly do not have that many inputs

---

### Post by Jcpayne on 2012-10-27
They are all 0bytes, are they just pointers? How are they 0 bytes?

---

### Post by Jcpayne on 2012-10-27
which event is defaulted to keyboard?

---

### Post by llamabr on 2012-10-27
[http://cjix.info/blog/misc/internal-input-event-handling-in-the-linux-kernel-and-the-android-userspace/](http://cjix.info/blog/misc/internal-input-event-handling-in-the-linux-kernel-and-the-android-userspace/)

What are you trying to do?

---

### Post by Jcpayne on 2012-10-28
Run software that requires keyboard input, but I can't figure out which eventX would be the keyboard input

---

### Post by deadflowr on 2012-10-28
cd into the by-path route, then ls -alt.

---

