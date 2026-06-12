---
title: "xdg-open stopped working since 16.04 upgrade"
date: 2016-05-30
forum: General Help
---

### Post by beauxq on 2016-05-30
```
xdg-mime query default inode/directory
```

gives me:

```
nemo.desktop
```

like I want it to.

But

```
xdg-open $HOME
```

Gives an error:

```
xdg-mime: mimetype argument missing
Try 'xdg-mime --help' for more information.
Unescaped left brace in regex is deprecated, passed through in regex; marked by <-- HERE in m/%{ <-- HERE (.*?)}/ at /usr/bin/run-mailcap line 528.
Warning: program returned non-zero exit code #66

```

And opens Audacious.

I tried editing the run-mailcap line to escape the braces, and that gets rid of that error message. But it doesn't fix the problem.
I still get "mimetype argument missing" and the wrong program opens.

---

