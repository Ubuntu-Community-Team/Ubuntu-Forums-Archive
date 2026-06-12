---
title: "Experiencing weird errors after running cp command"
date: 2013-02-26
forum: General Help
---

### Post by slosd on 2013-02-26
Hi, I really need some help on this...

**EDIT**: Posted too early... a script watching this folder messed with the files copied to "/a/b/c" and changed their permissions. If that file happened to be a symbolic link, the change was made for the file the link points to...

I just accidentally executed this command:
```
cp -ur "/" "/a/b/c"
```
As one would expect, it started copying everything in root to "/a/b/c". When I noticed that I wasn't running the command I actually wanted to I simply pressed CTRL+C to kill the program. It had already copied parts of /bin, /sys etc.

Right after that I started to get weird error messages:
```

$ vim asdf.sh
  Command not found
$ awk
  -bash: /usr/bin/awk: Permission denied
$ nano
  -bash: /usr/bin/nano: Permission denied
$ less
  -bash: /usr/bin/less: Permission denied
$ man xargs
  man: can't execute pager: Permission denied

```
and so on...
I then reinstalled vim and was able to use it again, but I'm not sure if reinstalling all packages will fix this. I would rather like to find out what the actual problem is...

Any idea what happened there? How can *cp* have any influence on the files it's copying? How do I fix this mess?

Thanks!

---

### Post by papibe on 2013-02-26
Hi slosd.

Is "/a/b/c" just that, or a short for the actual destination?

Regards.

---

