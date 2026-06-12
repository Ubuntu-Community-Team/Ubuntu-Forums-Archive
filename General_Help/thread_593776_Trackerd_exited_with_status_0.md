---
title: "Trackerd exited with status 0"
date: 2007-10-27
forum: General Help
---

### Post by sicofante on 2007-10-27
I'm getting this message in a dialog box when doing a search:

```

Could not send the search request

Process /usr/bin/trackerd exited with status 0
```

What's that supposed to mean?

I can't search anymore.

---

### Post by FredB on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148118](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148118) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Looks like there is two trackerd at the same time.

Try this :

killall -9 trackerd

And launch again trackerd.

It is a known bug on launchpad, bug 148118.

---

### Post by sicofante on 2007-10-28
Thanks FredB, I'll follow the issue on Launchpad.

---

### Post by tak1150 on 2007-10-30
is there a permanent solution to this? Rather than killing trackerd every time...

---

