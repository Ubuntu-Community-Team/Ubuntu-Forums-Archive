---
title: "why doe i have a black screen when i maximize windows?"
date: 2008-02-23
forum: General Help
---

### Post by byfly13 on 2008-02-23
Everytime i maximze a window in firefox it comes up black and i dont know why is there some way to fix this?

---

### Post by toa on 2008-02-23
Whats the content of the window, video, text, image ...

might be resolution or graphics !!

---

### Post by byfly13 on 2008-02-23
anything that is in a window so far that i have tried doesn't even matter what it is even documents.

---

### Post by toa on 2008-02-23
> **byfly13 said:**
> anything that is in a window so far that i have tried doesn't even matter what it is even documents.

is it only in firefox ? usually firefox is very stable app, try wih Opera if the same problem exists and other apps.

---

### Post by byfly13 on 2008-02-23
its not just firefox it is all my windows.

---

### Post by toa on 2008-02-23
> **byfly13 said:**
> its not just firefox it is all my windows.

makes more sense to have all the windows behave the same, which brings us back to your graphic cards settings and drivers

---

### Post by byfly13 on 2008-02-23
I have an Nvidia geforce mx/mx 400 graphics card and i dont think the drivers are supported by linux. what do i do? are they supported?

---

### Post by ShodanjoDM on 2008-02-23
They are. Even older Nvidia cards are still supported (with nvidia-glx-legacy driver). For your card, run this in the terminal:

```
sudo aptitude install nvidia-glx
```

---

### Post by dragonwings on 2008-02-23
try deactivate descktop effects .

---

### Post by byfly13 on 2008-02-23
ok it is instlled now what?

---

### Post by dmaynard on 2008-03-22
I had the same problem on a Dell Latitude D800.
dragonwings suggestion fixed my problem.
So try turning off screen effects by going to System->Preferences->Appearance
then select the Visual Effects tab and select None.

Good luck.

---

