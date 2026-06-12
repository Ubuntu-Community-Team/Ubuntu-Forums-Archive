---
title: "gdm does not start after upgrade to feisty"
date: 2007-04-26
forum: General Help
---

### Post by sambitnayak on 2007-04-26
Hi folks,

I upgraded from edgy to feisty y'day. The upgrade was complete without any problems and the machine restarted after that. On the first boot into feisty, the gdm tries to start, but it just gets hung probably and I only see a "waiting" mouse cursor.

I tried restarting the gdm by hitting ctrl+alt+backspace, but that did not solve the issue. The gdm hung again with the "waiting" mouse cursor staring at me :(

So, I went onto one of the virtual consoles (hit ctrl+alt+f1) and started kde, with startx on another display (my .xinitrc execs startkde). KDE started fine. I heaved a sigh of relief, and thought to see whats happening with the gdm. I am not very familiar with the diagnostic tools, but I just used strace to see what gdm was doing.

$ ps -ef | grep gdm
root      5350     1  0 14:27 ?        00:00:00 /usr/sbin/gdm
root      6895  5350  0 14:31 ?        00:00:00 /usr/sbin/gdm
root      6897  6895  0 14:31 tty7     00:00:03 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
gdm       6911  6895 93 14:31 ?        00:19:16 /usr/sbin/gdm
sambit    7215  7044  0 14:52 pts/1    00:00:00 grep gdm
$ pstree 5350
gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
                        &#9492;&#9472;gdm
$ sudo strace -p 6911
..........
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
select(8, [7], NULL, NULL, NULL)        = -1 EBADF (Bad file descriptor)
........

Any clues?

Thanks & Regards,
Sambit

---

### Post by Sef on 2007-04-26
If you have the internet working, then try this:

```
sudo aptitude update
```

```
sudo aptitude install ubuntu-desktop
```

---

