---
title: "Cursor Jumping around"
date: 2005-04-08
forum: General Help
---

### Post by amin_od on 2005-04-08
Hi,
I'm using Hoary on Acer Laptop Aspire 1680. If I type in any text editor except console text editor such as vim, then the cursor sometimes jumping around on the screen, so it really disturb me. Even when I type this msg, my cursor sometimes going up. The only way I can avoid this is by slowing down typing, console typing, M$ Windows (oh no). Anybody knows what kind of problem is this ?

thx

---

### Post by p!=f on 2005-04-08
Try to add
```

Option "HWCursor" "false"

```
to your /etc/X11/xorg.conf, section Device
more here:
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#extraxpointer](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#extraxpointer)

---

### Post by linuxgirlnerd on 2007-09-11
I am using Fiesty Fawn on a Dell Inspiron 6000 and having the same problem of the mousing cursor jumping around when I type. Does someone know how to fix this?:confused:

---

### Post by Michl on 2007-10-30
DId the xorg edit work for anyone?  Hate to edit the xorg file unless there
is some evidence this works.  Have the same problem on my Dell Latitude
laptop (but only there).

---

### Post by Michl on 2007-12-05
Anyone?

---

