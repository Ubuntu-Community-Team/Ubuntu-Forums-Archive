---
title: "Making programs independant of terminal"
date: 2007-08-17
forum: General Help
---

### Post by guguma on 2007-08-17
Hello and good days,

I have wine and utorrent installed, and I have made alias for it

```
alias torrent='wine /manythings/utorrent.exe'
```

when I use 

```
torrent &
```

utorrent executes fine, but when I close the terminal window it gets closed too. 

what am I doing wrong?

---

### Post by Seisen on 2007-08-17
You closed the terminal window, you can try Alt+F2 then enter ```
torrent &
``` and see if that works.

---

### Post by guguma on 2007-08-17
Allright that will work fine but I am actually asking is that if there is a way to run something from the terminal and making it independent of it so that it will not close when I close the terminal.

---

### Post by Seisen on 2007-08-17
I don't think that is possible, the closest solution that I can think of is the one I recommended.

---

### Post by mali2297 on 2007-08-17
Before you close the terminal, type:
```

disown

```

---

### Post by guguma on 2007-08-17
That works fine. 

Thanks so much.

---

### Post by legatek on 2007-08-17
I got the following bit of code from another thread recently. Paste the following into your .bashrc:

```
# super stealth background launch
# disconnects from launching shell, keeps running until killed
function daemon
{
    (exec "$@" >&/dev/null &)
}

```

then to launch any program independent of the terminal, type:

```
daemon <program>
```

---

### Post by guguma on 2007-08-17
now thats interesting :)

Thanks.

---

### Post by Lord Illidan on 2007-08-17
Or else precede a command with nohup..such as nohup gedit or nohup wine. Nice tips btw.

---

### Post by bogolisk on 2007-08-17
nohup and disown are both excellent solutions but only for graphical programs that have no need for the terminal. For text-mode program such as rtorrent, an excellent solution is to use dtach.

start rtorrent
```

dtach -c /tmp/rtor rtorrent....

```

The above will start rtorrent under a pseudo-terminal. To disconnect from that pty (and the rtorrent session), just type Ctl-\.The rtorrent session would still run in the background. To reconnect to the running rtorrent session
```

dtach -a /tmp/rtor

```

It's great because you can start a rtorrent session. Go to work, and from work, ssh to your home machine, reconnect to the running rtorrent session, stop/start/add/remove torrents all easily as if you were at home.

Some old-timers might notice that's very similar to screen. In fact dtach is screen made-simple. It only provide the dtaching feature from screen using unix-socket.

---

### Post by bodhi.zazen on 2007-08-17
Well, another solution to your original question is called screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

Screen is helpful when ssh into servers as well.

---

