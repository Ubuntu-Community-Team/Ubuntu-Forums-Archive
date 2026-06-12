---
title: "[SOLVED] rsync won't transfer folders with foreign names"
date: 2008-03-19
forum: General Help
---

### Post by geo909 on 2008-03-19
Hello everybody,
I have a problem here:
I am trying to make a backup of my files to an external hard disk with rsync.
The thing is that I am Greek and many of my folders are named with Greek characters.
So, when I try to recursively rsync them, I get messages like the ones above:
```

[CENTER].
.
.[/CENTER]
TeX/&#931;&#965;&#957;&#940;&#961;&#964;&#951;&#963;&#951; &#950; &#947;&#953;&#945; &#960;&#959;&#955;&#965;&#974;&#957;&#965;&#956;&#945;/
rsync: recv_generator: mkdir "/media/FreeAgent Drive/TeX/&#931;&#965;&#957;&#940;&#961;&#964;&#951;&#963;&#951; &#950; &#947;&#953;&#945; &#960;&#959;&#955;&#965;&#974;&#957;&#965;&#956;&#945;" failed: Invalid or incomplete multibyte or wide character (84)
*** Skipping everything below this failed directory ***
[CENTER].
.
.[/CENTER]

```

..and as you see nothing is transfered fromt those folders.
Rsync works fine with any other folder I have in latin characters..

I guess there should be an option for this but couldn't find it in the rsync man page..

Any ideas?
Thanks in advance!

---

### Post by geo909 on 2008-03-20
Anybody?

---

### Post by geo909 on 2008-03-21
For some strange reason, one nice morning this got fixed..
Not sure what changes I've made.
:confused:

---

