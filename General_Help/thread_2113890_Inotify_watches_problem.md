---
title: "Inotify watches problem"
date: 2013-02-08
forum: General Help
---

### Post by yulaow on 2013-02-08
Hi all!
Hoping this is the right section, i have something to ask about ubuntu.
I'm a web developer and i set up a LAMP on my pc to just make tests before to upload the files into my webhosting.
Recently i had some problem using commands like "tailf" and similars (i use tailf just to see the error.log of apache with autorefresh)

When i try to run tailf i get often this message:
```
cannot add inotify watch (limit of inotify watches was reached).

```
And the program stops immediatly. I have to reboot all the system to get it working again and i really dunno why this is happening. I am using linux since 5-6 years and this is the first time i get this error
Anyone has any idea?

edit: uh i just remembered that at the same time i see this error with tailf, also dropbox signals some strange problem with inotify watches
```
try 'echo 100000 | sudo tee / proc/sys/fs/inotify/max_user_watches' and restart dropbox 
```
obviously this solution does not work

---

### Post by JKyleOKC on 2013-02-08
If that code is exactly what you typed in, the reason it fails to work is thhat you've got a space between "/" and "proc" that should not be there. However, get a command line, run "cat /proc/sys/fs/inotify/max_user_watches" and post its output, which should be a single number. On my system here it's "524288" which ought to be enough for most anything...

---

