---
title: "Compiz used to work, no doesn't, on Dell Inspiron 1300"
date: 2008-05-21
forum: General Help
---

### Post by diablo75 on 2008-05-21
A friend of mine has a Dell Inspiron 1300 (has an Intel integrated Media Accelerator 900 graphics card in it) which I set up for him.  Compiz was running just fine on his fresh 8.04 install when I gave it to him.  But recently, he said it stopped working (I don't know if he changed a setting or what...)

I asked him to view System>Preferences>Appearance>Effects, but when he tries to enable it says "Desktop effects cannot be enabled" without much more detail as to why.

So I'm a little stumped.  What could be causing this and how might I get it working again?

---

### Post by overdrank on 2008-05-21
> **diablo75 said:**
> A friend of mine has a Dell Inspiron 1300 (has an Intel integrated Media Accelerator 900 graphics card in it) which I set up for him.  Compiz was running just fine on his fresh 8.04 install when I gave it to him.  But recently, he said it stopped working (I don't know if he changed a setting or what...)

I asked him to view System>Preferences>Appearance>Effects, but when he tries to enable it says "Desktop effects cannot be enabled" without much more detail as to why.

So I'm a little stumped.  What could be causing this and how might I get it working again?

Well I would say start at the beginning and configure the xorg and see what driver is being used. Then ask your friend what changes and apps installed or updates.

---

### Post by diablo75 on 2008-05-21
> **overdrank said:**
> Well I would say start at the beginning and configure the xorg and see what driver is being used. Then ask your friend what changes and apps installed or updates.

What's the command for this again?  To reconfigure xorg?

---

### Post by overdrank on 2008-05-21
> **diablo75 said:**
> What's the command for this again?  To reconfigure xorg?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ssjlance on 2008-05-22
I had a similar issue when I was on 7.10. Upgrading everything seemed to fix it.

---

### Post by diablo75 on 2008-05-22
> **ssjlance said:**
> I had a similar issue when I was on 7.10. Upgrading everything seemed to fix it.

Well, this is a fresh install which used to work...

I'll reconfigure xorg when I get a chance...

---

### Post by Forlong on 2008-05-22
If it still fails, try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

