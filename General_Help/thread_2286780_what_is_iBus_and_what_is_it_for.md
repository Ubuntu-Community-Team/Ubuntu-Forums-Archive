---
title: "what is iBus and what is it for?"
date: 2015-07-14
forum: General Help
---

### Post by sam_baker2 on 2015-07-14
Hi,
I have just installed 14.04 LTS and I notice that a program called iBus ( ver 1.5.5 ) is in the panel.
Can anybody tell me what it is for and do I need it?
When I call it up from terminal, I get this:
```

Usage: ibus COMMAND [OPTION...]

Commands:
  engine         Set or get engine
  exit           Exit ibus-daemon
  list-engine    Show available engines
  watch          (Not implemented)
  restart        Restart ibus-daemon
  version        Show version
  read-cache     Show the content of registry cache
  write-cache    Create registry cache
  address        Print the D-Bus address of ibus-daemon
  help           Show this information


```

Thanks

---

### Post by Dennis N on 2015-07-14
iBus is explained in this article:
[https://wiki.archlinux.org/index.php/IBus](https://wiki.archlinux.org/index.php/IBus)
It's a system for using non-English languages. But, I don't believe it is part of the default install of Xubuntu 14.04 - at least it is not on mine. No idea how it got there on yours. If you use English only, then I believe it is safe to remove.

---

### Post by vasa1 on 2015-07-14
OP hasn't specified the *buntu flavor for some reason. Lubuntu 14.04 has iBus by default.

Some posts relating to iBus:
[http://ubuntuforums.org/showthread.php?t=2218568&highlight=ibus](http://ubuntuforums.org/showthread.php?t=2218568&highlight=ibus)
[http://ubuntuforums.org/showthread.php?t=2227109&highlight=ibus](http://ubuntuforums.org/showthread.php?t=2227109&highlight=ibus)
[http://ubuntuforums.org/showthread.php?t=2230897&highlight=ibus](http://ubuntuforums.org/showthread.php?t=2230897&highlight=ibus)

---

### Post by mc4man on 2015-07-14
He tagged it xubuntu but often that is unintended.
If not using I'd disable it as it has caused issues. It can be disabled in an **Ubuntu install **in System settings > Language support > Keyboard input method system > none

---

### Post by sam_baker2 on 2015-07-15
@vasa1 I am using xubuntu ( 64 desktop )  with the xfce 4.12 desktop. Before I did the upgrade, I had xfce 4.10 , but installed 4.12 afterward.

---

### Post by vasa1 on 2015-07-15
> **mc4man said:**
> He tagged it xubuntu ...
My bad for not noticing.

Anyway, here's another link from the Xubuntu users mailing list: [https://lists.ubuntu.com/archives/xubuntu-users/2014-June/date.html](https://lists.ubuntu.com/archives/xubuntu-users/2014-June/date.html). It has some posts on the iBus issue.

---

