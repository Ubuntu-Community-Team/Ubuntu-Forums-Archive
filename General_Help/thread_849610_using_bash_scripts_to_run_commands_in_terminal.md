---
title: "using bash scripts to run commands in terminal"
date: 2008-07-04
forum: General Help
---

### Post by sipickles on 2008-07-04
Hi,

I am trying to run a command in a terminal using a bash script.

Here's my script:
```
#!/bin/sh
gnome-terminal -x python ZONE.py alpha
```

I want this to run ZONE.py in a python interpreter terminal with 'alpha' as an argument.

When run, the terminal instantly closes. The man page of gnome-terminal says:

```
 -x, --execute    Execute the remainder of the command line inside the terminal.
```

This is obviously not happening!

Any ideas?

Thanks

Si

---

### Post by sipickles on 2008-07-04
Sorry , it was a python path issue.

Why do these forums not allow you to delete posts?

---

