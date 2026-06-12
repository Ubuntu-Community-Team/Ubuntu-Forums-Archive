---
title: "Is my computer able to run beryl?"
date: 2007-01-27
forum: General Help
---

### Post by shironeko on 2007-01-27
I recently installed Beryl with AIGLX, but it seems to be sometimes slow. When opening new windows for example, the animation is not smooth at all.

Here are the specs of my computer:

Ubuntu x86 Generic Kernel (Edgy 6.10)
AMD athlon 64 3000+
512 MB RAM
ATI X300
---------------

Do I need more Ram? A better graphic Card? 
Is there some configuration I can do in order to optimize Beryl?
What about the Driver?

---

### Post by ENN0 on 2007-01-27
yes

---

### Post by shironeko on 2007-01-27
> **ENN0 said:**
> yes

Thanks, but why does it slowdown sometimes?
Is there something I can do? Something I can check?

---

### Post by Waappu on 2007-01-27
Hi

Try to disable e.g. blur plug-in. Disable panel animations
```
gconf-editor
```
go to apps->panle->global and uncheck enable_animations

Also changes to /etc/X11/xorg.conf file may help. Here is my [xorg.conf]("http://koti.mbnet.fi/waappu/download/xorg.conf") for example.
And here is guide that I have followed:
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Hope this helps

---

### Post by CheeseEatingBulldog on 2007-01-27
You should be, I am running an old 1300+ machine and beryl runs fine.

---

### Post by shironeko on 2007-02-02
Thank you very much. Runs 95% fine now ^^
Anyways, I'm gonna change my graphic card from Ati to nVidia. I heard they perform better.

---

