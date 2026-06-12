---
title: "Tmux help"
date: 2014-02-04
forum: General Help
---

### Post by curtis6 on 2014-02-04
Is there anyway to send a plain text command to a tmux session?

---

### Post by Lars Noodén on 2014-02-05
Yes.  Look at [send-keys](http://manpages.ubuntu.com/manpages/saucy/en/man1/tmux.1.html).  This below runs 'date' on the default session.  The C-m is a new line.

```

tmux send-keys  "date" C-m

```

If you have multiple sessions, you can use **-t** to specify a particular session by name.

```

tmux send-keys -t foo  "date" C-m

```

---

### Post by curtis6 on 2014-02-05
"User@NixBoxr:~$ tmux send-keys -t /tmp/pair "stop" C-m
failed to connect to server: No such file or directory"

I just keep getting that

---

### Post by Lars Noodén on 2014-02-06
> **curtis6 said:**
> "User@NixBoxr:~$ tmux send-keys -t /tmp/pair "stop" C-m
failed to connect to server: No such file or directory"

I just keep getting that

1.  You have to have tmux running already to use send-keys.

2.  To use sendkeys -t you have to have a real session name.  Did you launch tmux elsewhere creating a session named /tmp/pair?  It's a strange name to have for a session.  

```

tmux new -s /tmp/pair

```

If you want to create a new session and send input to it all at once, you can do that.

```

tmux new -s foo \; send-keys 'ls -lh' C-m

```

There the new session is called 'foo' but you could call it '/tmp/pair' instead.

---

