---
title: "How to show Quit... dialog?"
date: 2006-12-26
forum: General Help
---

### Post by oook on 2006-12-26
Hi,

What command can I run to show the Gnome System --> Quit... dialog (the one that lets you choose whether to log off, switch user,lock screen or power down)?  I want to link it to my keyboard's Log Off button.

Thanks

---

### Post by rlozano on 2006-12-26
right click on the panel and choose add to panel option then choose Quit icon. that should do it for you if i understood you correctly. :-)

---

### Post by oook on 2006-12-26
Thanks for the reply, but I need an actual command line that I can use to show the dialog.

---

### Post by rlozano on 2006-12-26
see if this will help you. at the terminal you can type shutdown --help

---

### Post by oook on 2006-12-26
As a last resort I'll use shutdown, but the GUI would be much cooler

---

### Post by lmo on 2007-01-03
I found:
```

  if [ -n "`pidof xfce4-session`" ]; then
    xfce4-session-logout
  elif [ -n "`pidof gnome-session`" ]; then
    gnome-session-save --kill --gui
  fi

```

So, if you is gnome is
```

   gnome-session-save --kill --gui

```

I also found straight logout immediately with no questions:
```

  skill -u `whoami`

```

---

