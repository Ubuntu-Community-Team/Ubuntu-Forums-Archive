---
title: "[SOLVED] Broken H Key"
date: 2008-02-20
forum: General Help
---

### Post by s0m31john on 2008-02-20
My H key is broken, won't work at all. Right now I have to copy and paste an "h" when I'm typing.

In windows I used some registry editor to make my insert key act as an "H".

Is is possible to do in 7.10, if so How should I go about doing it?

---

### Post by socceroos on 2008-02-20
> **s0m31john said:**
> My H key is broken, won't work at all. Right now I have to copy and paste an "h" when I'm typing.

In windows I used some registry editor to make my insert key act as an "H".

Is is possible to do in 7.10, if so How should I go about doing it?

LOOOOOOL.

Are you able to buy a new keyboard? You know, you can pick them up for about $10......

BUT, if you can't get another keyboard then I suggest you have a look at this. It looks like it will work well.

But it requires some file editing and command line work. If you get stuck then give us a hoy! :)

[http://blog.dotkam.com/2007/06/25/custom-keyboard-layout-in-ubuntu-or-just-linux/](http://blog.dotkam.com/2007/06/25/custom-keyboard-layout-in-ubuntu-or-just-linux/)

---

### Post by s0m31john on 2008-02-20
My computer is a laptop, so a new keyboard would be out of my price range.

I tried that doing what was in that blog, but it was a little much for me.

I got stuck after you type in  ```
sudo vi us
```

I can't find the "Insert" key on the list, and wouldn't know how to edit it if I did find it.

Anyway you can think of that uses a bit more GUI?

---

### Post by socceroos on 2008-02-20
Ok, I've found an easier way to do it.

Open up a terminal (Applications->Accessories->Terminal) and type in the following two commands, one at a time:



xmodmap -e "keysym Insert = h"
echo -e "keysym Insert = h" > ~/.Xmodmap



This should work straight away. It works for me!

Let me know how you go!

---

### Post by s0m31john on 2008-02-20
Thanks! Worked perfectly.

---

