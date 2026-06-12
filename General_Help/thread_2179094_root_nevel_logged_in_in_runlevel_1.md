---
title: "root nevel logged in in runlevel 1?"
date: 2013-10-06
forum: General Help
---

### Post by clearski on 2013-10-06
Hi, everyone.

I came across with something that looks strange while playing with runlevels.

I'm in a runlevel 2 state, as almost everybody else here :),  I am using telinit to switch to runlevel 1. The system goes into single user mode - as root. I do my stuff and then I switch back to runlevel 2.

After that, I open a CLI and do the check:

```
lastlog | grep root
```

But I got

```
root                         **Never logged in**
```

How is it possible, as I just came back from the root prompt? Needless to say, the root account is not enabled.

---

