---
title: "[SOLVED] writing to read only files (linux-restricted-modules-common)"
date: 2007-09-16
forum: General Help
---

### Post by Rozenrot on 2007-09-16
I've been trying to get the newest drivers for my video card (ATi x800) and I need to modify the file "linux-restricted-modules-common" (ect/default) and I need to make the DISABLED_MODULES="" have something in it.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87)

Now here's my problem; one, how do I get it to not be a read only file (only root can change this?) and two, what do I actually put in DISABLED_MODULES="", do I put somemodule2 fglrx or do I put something else?

:confused:

---

### Post by nowshining on 2007-09-16
edit: open up a terminal - applications - Accessories - terminal

gksudo nautilus

input your password

filesystem on left

etc then default

then

find the file

Right click or double click and click display or if right clicking click open with text editor.

---

### Post by nowshining on 2007-09-16
or it gives the command here

```


gksudo gedit /etc/default/linux-restricted-modules-common
or, on Kubuntu,
kdesu kate /etc/default/linux-restricted-modules-common

We need to add fglrx (only! don't remove anything!) to this:
DISABLED_MODULES="somemodule2 fglrx"

```

either sudo or gksudo - it depends on which way you choose, i just let you go by point and click

for the rest as to what to put in the disable modules I really don't know I: don't have an ATI card.

---

### Post by Rozenrot on 2007-09-16
Thanks!

As you can tell, I'm fairly new to this, but with people like you helping me, I'm learning tons every day! :D

---

### Post by nowshining on 2007-09-16
oh you'll get used to it and soon itta become natural best way to remember commands is to not copy + paste but to type each letter out. :)

Again you'll learn quite fast and Again it will become natural after a month or two.

---

### Post by Rozenrot on 2007-09-16
Really? I'll start typing out my commands then instead.  And I've already learned so much in these past few days.  Plus when you get stuff to work you feel really accomplished >_>.  Now that my video card works, I'm going to enable my dual monitor set up :D

Thanks for your help!:guitar:

---

### Post by nowshining on 2007-09-16
lolz ur welcome. :) yeah in linux u'll be doing terminal commands A LOT compared to windows and prob. MAC - :) so get used to them. And if you want you can go to Thread Tools and mark this thread as solved.

---

