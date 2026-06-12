---
title: "Running commands into another users Screen"
date: 2015-10-15
forum: General Help
---

### Post by Lexicade on 2015-10-15
Hi,

Im trying to run a command into another users screen on my server.

Ive done :acladd user and :multiuser on. 
The command i'm using is:
```
screen -x user/screenname -X echo foobar
```

And it outputs:
```
Cannot opendir /var/run/screen/S-user: Permission denied
```

I tried changing permissions but screen refuses to co-operate if the permissions for the /var/run/screen/ folder have changed.
Anyone got any ideas on this?

---

### Post by Lars Noodén on 2015-10-15
I gather that screen has to be run [suid root](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Remote_Processes#screen.281.29) for that.  The error I get when trying multiuser mode without it is : "Must run suid root for multiuser support."

You can also do multiuser in tmux by sharing the socket with write access to the appropriate group.

---

