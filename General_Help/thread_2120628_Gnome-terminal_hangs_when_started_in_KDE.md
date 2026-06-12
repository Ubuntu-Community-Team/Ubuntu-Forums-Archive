---
title: "Gnome-terminal hangs when started in KDE"
date: 2013-02-27
forum: General Help
---

### Post by cole.mickens on 2013-02-27
[http://askubuntu.com/questions/251028/gnome-terminal-hangs-on-start-in-kde/261826#261826](http://askubuntu.com/questions/251028/gnome-terminal-hangs-on-start-in-kde/261826#261826)

Pretty much that issue tit-for-tat.

Of course gnome-terminal has no verbose mode so I'm out of ideas on what to debug.

---

### Post by ghost_ryder35 on 2013-05-10
I have the same issue.  Any one with troubleshooting tips out there?

---

### Post by sandyd on 2013-05-10
moved to general help

---

### Post by ghost_ryder35 on 2013-05-15
after some additional debugging, it looks like I can open 'konsole' and then start gnome-terminal as root by running

```
 sudo gnome-terminal 
```

I have some strace's and it looks like when trying to launch gnome-terminal as my regular user gnome-terminal gets stuck in a loop at
```

poll([{fd=6, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=6, revents=POLLOUT}])
writev(6, [{"( \4\0d\0\240\5\272\2\0\0\0\0\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=6, events=POLLIN}], 1, 4294967295) = 1 ([{fd=6, revents=POLLIN}])
recvfrom(6, "\1\1N\2\0\0\0\0%0\313\1\374\4\233\2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096, 0, NULL, NULL) = 32
recvfrom(6, 0x1a0e014, 4096, 0, 0, 0)   = -1 EAGAIN (Resource temporarily unavailable)
recvfrom(6, 0x1a0e014, 4096, 0, 0, 0)   = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=6, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=6, revents=POLLOUT}])
writev(6, [{"( \4\0d\0\240\5\272\2\0\0\177\2\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16

```

I'm no C++ coder so anyone with some incite here would be great.

---

