---
title: "Udoing XGL changes"
date: 2008-04-05
forum: General Help
---

### Post by Totz on 2008-04-05
I followed this guide but stuff doesn't function correctly for me with it, is there a way to undo these changes?

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by danwood76 on 2008-04-05
Which ATI card do you have?
If you have a fairly rescent one you dont need to install xgl.

To reove the xgl server type this in terminal:
```

sudo apt-get remove xserver-xgl

```
to remove the startup script do:
```

sudo rm /usr/share/xsessions/xgl.desktop

```

---

### Post by Totz on 2008-04-05
Thanks, its a brand new computer. I was trying to get the cube effect for windows but it caused all effects to stop, even after removing the XGL it still wont show the wobble effect which it did before :/

---

### Post by Totz on 2008-04-05
How about a code that can restore the graphic settings to default? I dont want to have lost  a nice feature when Ive only started using Ubuntu :p

---

