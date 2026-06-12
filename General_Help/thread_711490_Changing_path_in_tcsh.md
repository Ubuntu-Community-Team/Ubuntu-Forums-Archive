---
title: "Changing path in tcsh?"
date: 2008-02-29
forum: General Help
---

### Post by Tailkinker on 2008-02-29
I'd gotten used to tcsh in Slackware, but since Slackware doesn't like my new computer, I've switched to Ubuntu.  Now I have a problem:  I cannot find the tcsh startup script.  I want to edit my default paths, but I can't find the startup script.  Can anyone clue me in?

---

### Post by taurus on 2008-02-29
Do you have ~/.cshrc?  Otherwise, look in /etc for either cshrc or tcshrc.

```
ls -la /etc/*shrc
```

---

### Post by Tailkinker on 2008-02-29
That was the first place I looked, as it is where this info is found in Slackware.  However, the cshrc, and csh.login were bare of path commands (or of much of anything), and ~/.cshrc was routinely ignored.  As was ~/.tcshrc.

---

### Post by taurus on 2008-02-29
If you want to add a path to ~/.cshrc, then create one.

```
set path = (new_path more_path even_more_path)
```

---

### Post by Tailkinker on 2008-02-29
Tried adding the new path to ~/.cshrc, and to ~/.tcshrc, and it was ignored.

---

### Post by taurus on 2008-02-29
After you added in the new path, did you log out and back in again or at least rehash it?

```
source ~/.cshrc
-or-
source ~/.tcshrc
```

---

### Post by Tailkinker on 2008-03-01
I launched a new xterm to test it.  That works in slackware, but it seems that in Ubuntu, the source command is required.  Thanks.

---

