---
title: "Relocation Error"
date: 2008-03-16
forum: General Help
---

### Post by phoenix5002 on 2008-03-16
I have Tribes2 for linux, and when I run the game itself it runs just fine....
I do see this however in terminal:
[b]fcntl: Operation not permitted
fcntl: Operation not permitted[/b]
I see that when I start the game, and then the game runs good, but when I exit the game I see:
```
BUG! (Segmentation Fault)  Going down hard...
Tribes 2 for Linux #25034
Built with glibc-2.1 on x86
Stack dump:
{
        0xffffe420
        0x81d9834
        0x81d1bf3
        0x823d048
        0x81d7457
        0xb7ca3050
        0x8050b41
}
Please send a full bug report,
along with the contents of autosave to: support@lokigames.com
```

ok, so that's no big deal as the game runs fine....however, to play it online they made a program called "defense turret" which is an anti-cheat program, and it will run and then run the game.  NOTE: it still gives the [b]fcntl: Operation not permitted
fcntl: Operation not permitted[/b] messages in the terminal
but when I run defense turret (DT), it will crash the game when a map is loading, with an error **segfault inside DT!**


I did a lot of research and it appears that it's the glibc library.  Apparently the Ubuntu 7.10 ones are incompatible with the game.  I guess because it's older.  Anyway a solution to this problem I found is to make a folder called "Loki_Compat" or something, and put the required libraries in there:
Libraries:
[b]ld-linux.so.2  libdl.so    libm.so.6        libX11.so.6
libc.so.6      libdl.so.2  libpthread.so.0  libXext.so.6[/b]
then to make a shell script with the contents:
> COMPAT=/opt/games/Loki_Compat/

export LD_LIBRARY_PATH=$COMPAT
LD_ASSUME_KERNEL=2.2.5 $COMPAT/ld-linux.so.2 /opt/games/t2-linux/dt -nologin

that way it will run those older "compatible" libraries.
However, I will now get this error when trying to run the script

> ./tribes2: relocation error: /opt/games/Loki_Compat/libc.so.6: symbol _dl_starting_up, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference

---

### Post by phoenix5002 on 2008-03-16
maybe it has something to do with the fact that the script runs "dt -nologin" and then dt runs the program "tribes2", you can clearly see that "tribes2" is what's having the problem as that last error says.  just thinking.....

---

### Post by phoenix5002 on 2008-03-17
bump.

give this another chance.....

---

### Post by phoenix5002 on 2008-03-18
last bump....
anyone?

---

