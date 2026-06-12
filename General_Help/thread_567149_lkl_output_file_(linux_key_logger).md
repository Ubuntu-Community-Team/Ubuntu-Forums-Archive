---
title: "lkl output file (linux key logger)"
date: 2007-10-04
forum: General Help
---

### Post by phillips321 on 2007-10-04
Hi guys,

When i try to run lkl for some reason i dont get an output file created.

Here's the command i'm running
```
phillips321@LinuxDesktop:~$ sudo lkl -l -k '/usr/share/lkl/keymaps/us_km' -o /home/phillips321/keys.txt

```

any ideas on why the file isn't being created?

i've also tried

```
phillips321@LinuxDesktop:~$ sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o keys.txt

```

cheers in advance

---

### Post by Jeffers0n on 2008-05-20
I know this post is a little old but I am having the exact same problem.  I'm running Hardy and when I run lkl there is never any output generated.  I can see that lkl is doing something by running top, which shows that lkl is at 30% CPU usage.  Does anybody have any idea what might be going on?

---

