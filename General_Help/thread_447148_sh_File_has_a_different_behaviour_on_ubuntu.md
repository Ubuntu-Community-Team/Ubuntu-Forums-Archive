---
title: "sh File has a different behaviour on ubuntu?"
date: 2007-05-17
forum: General Help
---

### Post by muhu on 2007-05-17
Hello

I have an sh file that runs on OpenSuse without any Problems but when i let it run on Ubuntu errors occure?
```
 239: Syntax error: word unexpected (expecting "then")
```

thx

---

### Post by Delkster on 2007-05-17
> **muhu said:**
> I have an sh file that runs on OpenSuse without any Problems but when i let it run on Ubuntu errors occure?
```
 239: Syntax error: word unexpected (expecting "then")
```

My guess is that the script probably has bash-only syntax in it. In most Linux distros /bin/sh (the default shell for scripts) points to the bash shell (/bin/bash) but in Ubuntu it nowadays points to dash (/bin/dash). Both comply with the basic POSIX standard but bash has some extensions in addition to that. If your script has syntax that doesn't actually belong to POSIX but is a bash extension instead (so-called bashisms), it doesn't work in dash, or probably in any other shell than bash.

The fix is at the first line of the script where you declare what shell should be used for running the script. My guess is that it now says:
```
#!/bin/sh
```
but it really shouldn't say that if it has bash syntax since /bin/sh, the default shell for scripts, isn't necessarily bash. Since it happens to be bash in most distros, that happens to work there (and happens to fail on others, such as Ubuntu), but if the script has bashisms, it really should explicitly declare that the script needs to be run by bash and nothing else:
```
#!/bin/bash
```
or, even more compatible:
```
#!/usr/bin/env bash
```

Change the script so that it demands to be always run by bash, and it'll probably work.

---

### Post by muhu on 2007-05-18
hi - the first line says ```
#!/bin/bash
``` i tried your suggestions but still doesnt work?:confused:

---

### Post by IgnorantGuru on 2007-05-18
If you're running the file with 
```
sh somescript
```
it won't matter if the first line is #!/bin/bash - sh points to dash.  You have to run it with

```
./somescript
```
or
```
bash somescript
```

---

### Post by muhu on 2007-05-18
it works now! thx

---

