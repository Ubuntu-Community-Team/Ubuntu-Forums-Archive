---
title: "Terminal won't open"
date: 2018-07-27
forum: General Help
---

### Post by jecub on 2018-07-27
So I recently installed ubuntu 16.04 (xenial) on crouton, upgrading from 14.04 (trusty). When I went to access the terminal option, the mouse showed that it was loading, the icon on the sidebar showed up, then it disappeared. No error messages or anything? Any help? If it helps I use Unity as my DE.

Thanks!

---

### Post by #&amp;thj^% on 2018-07-27
You will need to go to a TTY session using keyboard combo <ctrl+alt+F2>
and then make a copy of the current file:
```

cp ~/.bashrc ~/Documents/.bashrc.bak
```

now recreate a fresh bashrc file with:

```

cp /etc/skel/.bashrc ~/
```
To get back to your graphical session use keyboard combo <ctrl+alt+F7>

---

