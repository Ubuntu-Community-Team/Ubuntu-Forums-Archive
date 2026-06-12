---
title: "Error when sudo-ing KDE apps [Resolved]"
date: 2007-05-12
forum: General Help
---

### Post by bullines on 2007-05-12
Hi!

I just installed Kubuntu (Feisty) and so far, everything's great.  One thing I noticed, though, was that if I run a command such as this:

sudo kate /path/to/some/file

I get the following message:

```

DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-6087' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

```

The app still runs.  But what could be causing this message?  Thanks in advance.

---

### Post by taurus on 2007-05-12
Try

```
**kdesu** kate /path/to/some/file
```

---

### Post by aysiu on 2007-05-12
Uh, never use *sudo kate*... ever.

Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Then, take Taurus's advice.

---

### Post by bullines on 2007-05-12
kdesu seems to do the trick.  Thanks :)

---

