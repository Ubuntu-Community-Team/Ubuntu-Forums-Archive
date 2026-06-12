---
title: "my p and o buttons are not working."
date: 2014-02-26
forum: General Help
---

### Post by sjoerdmeijer33 on 2014-02-26
as the title says please tell me how i fix it.

---

### Post by ian-weisser on 2014-02-26
Replace your keyboard?

---

### Post by Tinman131 on 2014-02-26
An alternative to full replacement will be to try to clean it out; I think most keyboard keys can be removed with minimal risk for structural damage (look your model up online).  Because the P and O keys are right next to each other, there might be something blocking the contacts (solid or dried liquid, perhaps).  If they really won't work and your keyboard will need replaced anyway, you won't necessarily be out anything.

---

### Post by sjoerdmeijer33 on 2014-02-26
its a s,ftware ,r,blem the ,umber ,f ,utt,,s ,,t w,r,i,g is i,cresi,g

---

### Post by ian-weisser on 2014-02-26
How did you determine that it's a software problem?
How did you rule out hardware?

---

### Post by Impavidus on 2014-02-26
Try booting from a (known good) live disk. If the problem is still there, it's hardware. If it's gone, it's software.

---

### Post by tgalati4 on 2014-02-27
Open a terminal and run *xev*.  Move the mouse into the *xev* box and type some keys.  Take note of the events.  You should have a key press event and a key release event for each key.  See if the keys are even being detected.  Also look in your log files for errors:

```
less /var/log/Xorg.0.log
less ~/.xsession-errors
```

You can run these by either logging into your machine from another linux machine using *ssh*, or try plugging in a USB keyboard.

---

