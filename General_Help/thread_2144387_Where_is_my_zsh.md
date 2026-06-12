---
title: "Where is my zsh?"
date: 2013-05-12
forum: General Help
---

### Post by postt on 2013-05-12
I just installed zsh.

"echo $SHELL" output is "/bin/zsh"

On the other hand, "which zsh" output is "/usr/bin/zsh"

So where is my zsh located, "/bin/zsh" or "/usr/bin/zsh"?

---

### Post by Ranko Kohime on 2013-05-12
Probably one is a symlink to the other.

/me goes to test

On my system, /bin/zsh is a symlink to /etc/alternatives/zsh, which is another symlink to /bin/zsh5, which is a binary.  /usr/bin/zsh is a symlink to /etc/alternatives/zsh-usrbin, which is another symlink to /bin/zsh5.

So I'm guessing the Zsh binary is /bin/zsh5.  :P


To discover what a file is, you can use these options for ls, followed by the file name.
```
ls -AhlF
```
The lower case 'l' at the left most block of info marks the file as a symlink.

The file name given is the path you just typed in, followed by ->, and then it shows the path the links connects to.  Keep doing that until you come to a file with a significant size that is not a symlink, and you probably have a binary.

```
lrwxrwxrwx 1 root root 21 Jan 23 23:26 /bin/zsh -> /etc/alternatives/zsh*
lrwxrwxrwx 1 root root 9 Jan 23 23:26 /etc/alternatives/zsh -> /bin/zsh5*
-rwxr-xr-x 1 root root 673K Sep 16  2012 /bin/zsh5*
lrwxrwxrwx 1 root root 28 Jan 23 23:26 /usr/bin/zsh -> /etc/alternatives/zsh-usrbin*
lrwxrwxrwx 1 root root 9 Jan 23 23:26 /etc/alternatives/zsh-usrbin -> /bin/zsh5*

```

---

### Post by evilsoup on 2013-05-12
By the way, if you're asking for the purposes of scripting, rather than just curiosity: you should use a shebang line like:

```

#! /usr/bin/env zsh

```

...if you're writing zsh scripts. This ensures that any scripts you make are portable across *nixes (as long as they have zsh installed).

---

