---
title: "Video Settings - Simple Question"
date: 2007-05-16
forum: General Help
---

### Post by Nubifier on 2007-05-16
Could anyone please tell me what the command is to restore my video settings to what they were when I first isntalled Ubuntu 7.04 Feisty?

Thanks,
  Nubi

---

### Post by taurus on 2007-05-16
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Nubifier on 2007-05-16
Alright, thanks for the reply but it looks like I was asking the wrong question, maybe someone can help me out a bit as to what I SHOULD be asking.

I get the message

Failed to start X server (your graphical interface). It is likely not set up correctly

Any idea what I can do to fix that?
I had Ubuntu installed for 3 days before messing around to much to get this error.

---

### Post by taurus on 2007-05-16
You need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
```
Use the default setting if you are not sure what the answer is for a question and use **vesa** driver for your graphic card for now until you get X up and running again.

---

### Post by Nubifier on 2007-05-16
Thanks a lot, X is going again.

---

