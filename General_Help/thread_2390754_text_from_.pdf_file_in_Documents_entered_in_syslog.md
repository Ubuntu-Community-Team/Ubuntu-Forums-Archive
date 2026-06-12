---
title: "text from .pdf file in Documents entered in syslog during bootup?!?"
date: 2018-05-02
forum: General Help
---

### Post by AR_Kozz on 2018-05-02
Poking through /etc/syslog yesterday I noticed strange text that I recognized was from a .pdf file in my home/me/Documents folder.

Everything looks pretty normal up till then. From two preceding lines (with time recalibrated with the 1st line at 0 seconds)

```
0 gnome-session[2085]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
9 gnome-session[2085]: (tracker-extract:2266): Tracker-WARNING **: Task 0, error: at most 64 tables in a join
9 gnome-session[2085]: Sparql was:
9 gnome-session[2085]: INSERT { GRAPH <urn:uuid:######-###-###-####-#############> { _:tag a nao:Tag ; nao:prefLabel "(text text text text text text text) .25X1\r\n /~~ ~ ~\r\n Rc" }  }
9 gnome-session[2085]: WHERE { FILTER (NOT EXISTS { ?tag a nao:Tag ; nao:prefLabel "(text text text text text text text text text text) .25X1\r\n /~~ ~ ~\r\n Rc" }) }
```

And the last 2 lines repeated a bunch of times until pretty much the entire file was dumped into the syslog.

How do I figure out what the hell gnome-session was thinking? Is it a result of the immediately preceding join error?

---

