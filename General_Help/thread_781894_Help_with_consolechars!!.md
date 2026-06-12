---
title: "Help with consolechars!!"
date: 2008-05-04
forum: General Help
---

### Post by blithen on 2008-05-04
All I'm trying to do is run this command
```
blithen@sparky:~/Desktop$ consolechars -f Uni3-Terminus16.psf
```
and the error I get is this
```
Couldnt get a file descriptor referring to the console
get_console_fd: Invalid argument
```
Any help at all would be appreciated.

---

### Post by unutbu on 2008-05-04
Try 
```
CTRL-ALT-F2
consolechars -f Uni3-Terminus16.psf
```

The command only works at a virtual terminal. It doesn't work inside X.

---

### Post by blithen on 2008-05-04
> **unutbu said:**
> Try 
```
CTRL-ALT-F2
consolechars -f Uni3-Terminus16.psf
```

The command only works at a virtual terminal. It doesn't work inside X.

Oh...well...that's crap. x.x Thanks for the help though!

---

