---
title: "New Kernel Messed Up My Computer"
date: 2017-03-23
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-03-23
I installed updates on two computer, both the screen resolution is stuck at 1280x768, like there isn't a video driver, nor will my wireless mouse/keyboard work or Internet.
It's the kernel ending in .70


I tried booting into the previous kernel and it worked the first time, the second time, I got black screen with text telling me to ctrl+d to continue and it's broken.
I tried recovery and fixed the grup and now I can't get into either, the latest one, the screen stays purple.

Now I have to back up everything and reinstall with a kernel from some wheres else.

---

### Post by QIII on 2017-03-23
What release of Ubuntu and what is the rest of the kernel version number?

---

### Post by ThePowerpuffGirls on 2017-03-24
I'm not sure what the full kernel number is, I believe it was 4.4.0.70. I'm not sure how to check it. I have Ubuntu 16.04 (x64)
I solved the problem by downloading a newer kernel from a newer version of Ubuntu. I currently have 4.9.17-040917-generic (AMD/64).
I did it on another computer before downloading the updates, however it still downlowds the latest kernel for 16.04 anyways, however it uses the latest one overall.

When I ran my script (right word?), to install a bunch of software after a reinstall, I have a command that removes the old kernels but I didn't see that one listed for removal; the one that made my computer go weird.

---

### Post by howefield on 2017-03-24
Glad you got it sorted but for future reference you'll probably find the kernel in use listed in System Settings > Details > Graphics..

[ATTACH=CONFIG]274285[/ATTACH]

or from the terminal command..

```
uname -r
```

Eg,
```
uname -r
4.10.0-13-generic
```

---

### Post by ThePowerpuffGirls on 2017-03-24
Thank you.
It only shows the the kernel it is currently using with uname -r, you wanted the one that messed up my computer, yes?
Also, for some reason under 'graphics', it just says 'Intel® Haswell'.

---

