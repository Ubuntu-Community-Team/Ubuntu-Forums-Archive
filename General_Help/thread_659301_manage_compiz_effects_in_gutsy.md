---
title: "manage compiz effects in gutsy?"
date: 2008-01-05
forum: General Help
---

### Post by 99bluefoxx on 2008-01-05
how do i do this?
i want my 3D desktop switching and wobbly windows/transparent windows back
i found the compiz effects manager but i still dont have the 3d desktop switching, still the same thing as default
also i dont ahve the wobblie windows, yet they still wont give me my effects
if i could get some fixxes for this, as my friends are coming by and i want them to see it in all its glory X3

---

### Post by ~LoKe on 2008-01-05
If you've got CCSM installed, then you should be able to do this.  Open it up, and on the right there will by a bunch of options with checkboxes next to them.  Tick the box next to "Desktop Cube," "Rotate Cube" and "Wobbly Windows".

If you don't have CCSM:
```
sudo apt-get install compizconfig-settings-manager
```
```
ccsm &
```

---

### Post by conehead77 on 2008-01-05
This blog should answer all your questions:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by 99bluefoxx on 2008-01-05
thats what i did, it still didnt work

---

### Post by 99bluefoxx on 2008-01-05
> **conehead77 said:**
> This blog should answer all your questions:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
allready been there, didnt work

---

### Post by ~LoKe on 2008-01-05
> **99bluefoxx said:**
> allready been there, didnt work

Type this into the terminal:
```
compiz --replace
```

---

### Post by 99bluefoxx on 2008-01-05
failed my computer, took forever to get back onto my desktop after too
when i origionally upgraded my ubuntu i lost the window borders and had to use ```
 metacity --replace
``` to get them back
i placed this command onto my startup items as it was the only fix i could find
if i cant fix it is there a way to downgrade back to feisty w/o reinstalling?

---

### Post by 99bluefoxx on 2008-01-05
ok, found my problem
i didnt have the "custom effects" box enabled in the system>preferences>appearance app, got it working now, just have to find all the new features
flame and water are awesome, as is middlemouse+drag on desktop X3
ubuntu rox, i think my friends will be pleased

---

