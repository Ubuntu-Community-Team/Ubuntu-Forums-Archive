---
title: "Question on the number of users logged in currently"
date: 2008-02-06
forum: General Help
---

### Post by imbjr on 2008-02-06
The users command tells me I am logged in twice - which I am familar with the idea of (an X session and the very terminal session used to issue the command).

However, uptime tells me 4 users are logged in. Now I can account for the 3rd user. That will be me again using the screen command to run a long, long, long, long render job. But the 4th user? Who is that?

---

### Post by TidusBlade on 2008-02-06
Maybe you are running a session you are not aware of? Or the tiny possibility of someone else logged into your computer, might be through SSH if you do it on another computer.

---

### Post by kostkon on 2008-02-06
It must be the *root* user.

---

### Post by Martin Witte on 2008-02-06
in a terminal window I see
```
martin@toshibap200:~$ uptime
 20:03:27 up  1:08,  2 users,  load average: 0.34, 0.17, 0.18
martin@toshibap200:~$ who -T
martin   + tty7         2008-02-06 18:55 (:0)
martin   + pts/0        2008-02-06 20:03 (:0.0)
```
when I open another terminal I get
```
martin@toshibap200:~$ uptime
 20:05:57 up  1:10,  3 users,  load average: 0.35, 0.28, 0.22
martin@toshibap200:~$ who -T
martin   + tty7         2008-02-06 18:55 (:0)
martin   + pts/0        2008-02-06 20:03 (:0.0)
martin   + pts/1        2008-02-06 20:05 (:0.0)

```
I believe tty7 is the shell to start the login process and X, as a view on ps -ef shows
```
martin@toshibap200:~$ ps -ef|grep tty7
root      5043  5038  7 18:55 tty7     00:05:55 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
martin    6661  6446  0 20:10 pts/1    00:00:00 grep tty7
```
maybe a true ubuntu expert can shine a brighter light on this

---

### Post by imT on 2008-02-06
i see the same crap
```
imT@ubpc:~$ who -T
imT   + tty7         2008-02-05 11:27 (:0)
imT   + pts/0        2008-02-06 21:14 (:0.0)

```

---

### Post by imbjr on 2008-02-06
This what I see:

> 
imbjr@pc:~$who -T
imbjr    + tty7         2008-02-06 16:46 (:0)
imbjr    + pts/0        2008-02-06 23:17 (:1.0)
imbjr@pc:~$uptime
 23:17:51 up 1 day, 13:59,  4 users,  load average: 2.12, 2.28, 2.32


So that's tty7 for the X session, pts/0 for the terminal session in which I just ran the commands.

But uptime says 4 users. Well one may be a screen session for my long render. But the 4th - erm. Dunno.

However ...

Now this looks better:
> 
imbjr@pc:~$who -a
           system boot  2008-02-05 09:26
           run-level 2  2008-02-05 09:26                   last=
LOGIN      tty4         2008-02-05 09:26              4664 id=4
LOGIN      tty5         2008-02-05 09:26              4665 id=5
LOGIN      tty2         2008-02-05 09:26              4667 id=2
LOGIN      tty3         2008-02-05 09:26              4670 id=3
LOGIN      tty6         2008-02-05 09:26              4672 id=6
imbjr    + tty7         2008-02-06 16:46   .         17639 (:0)
imbjr    + pts/0        2008-02-06 23:17   .         20154 (:1.0)
           pts/1        2008-02-06 23:06             20022 id=/1    term=0 exit=0
           pts/2        2008-02-06 19:37                 0 id=/2    term=0 exit=0
LOGIN      tty1         2008-02-05 18:04             14459 id=1
           pts/4        2008-02-05 23:36             17012 id=/4    term=0 exit=0
LOGIN      tty1         2008-02-06 00:03             17320 id=1


I can see 4 of me now. Looks like maybe a terminal session is lurking.

---

