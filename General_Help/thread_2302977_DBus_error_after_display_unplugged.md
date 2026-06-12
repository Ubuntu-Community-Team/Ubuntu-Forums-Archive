---
title: "DBus error after display unplugged"
date: 2015-11-15
forum: General Help
---

### Post by whatthefunk on 2015-11-15
I accidentally unplugged one of my displays while a video was running on it and my desktop crashed.  I tried rebooting and restarting plasmashell (using Kubuntu 15.04), but nothing is working. I just have a black screen at the moment. Im getting the following error:
```

     org.freedesktop.DBus.Error.NoReply : Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 

```

How can I clear this up?

---

### Post by ian-weisser on 2015-11-15
Do you get the error before logging in, or after logging in?

---

### Post by whatthefunk on 2015-11-15
Finally solved this.  All I had to do was move .config/plasma and let plasma rebuild it.
```

~$ mkdir -p plasma
~$ mv .config/plasma* plasma/

```

---

