---
title: "Firefox Fonts"
date: 2007-04-12
forum: General Help
---

### Post by justin on 2007-04-12
Recently, my firefox fonts have become quite ugly, and this seemed to have happened on its own.

[IMG]http://img373.imageshack.us/img373/9670/ff2us9.png[/IMG]

How can I make my fonts in firefox anti-aliased again?

NOTE: installing msttcorefonts didn't work.

---

### Post by introspectif on 2007-04-12
When I got this once before, what I did was:

```
sudo dpkg-reconfigure fontconfig-config
```

and when it came to the screen which asked whether to 'use bitmapped fonts', choose 'no'.

Hope it helps :)

---

### Post by justin on 2007-04-12
Worked great. Thanks!

---

### Post by Jeremy Jackins on 2007-04-12
I'm having the same problem, but the dpkg-reconfigure solution isn't working for me.
any other ideas?

---

