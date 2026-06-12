---
title: "changing sftp default directory"
date: 2015-12-20
forum: General Help
---

### Post by sniper8752 on 2015-12-20
When I sftp to my server, it puts me in my user folder.  How do I change the directory to where the files I want to work with are?

---

### Post by sudodus on 2015-12-20
I assume you mean the current directory in the remote computer.

You can do it when you start sftp (which is a good idea, if often you want to go to the same directory, because you can make an alias for it)

or you can do it while you are running sftp with a cd command, that looks like the normal cd command in the terminal window (bash shell).

Examples:

```
sftp sniper@192.168.0.2:/home/sniper/Downloads
```

or from your home directory alias user folder

```
sftp> cd Downloads
```

or from anywhere

```
sftp> cd /home/sniper/Downloads
```

Example of alias:

```
alias sdl='sftp sniper@192.168.0.2:/home/sniper/Downloads'
```

---

