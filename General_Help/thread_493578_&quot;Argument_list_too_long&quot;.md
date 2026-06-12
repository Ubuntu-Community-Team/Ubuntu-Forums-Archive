---
title: "&quot;Argument list too long&quot;"
date: 2007-07-05
forum: General Help
---

### Post by vxbinaca on 2007-07-05
$ cd ~/.Trash && wipe *.*
bash: /usr/bin/wipe: Argument list too long
$

I've been holding off posting here as I like to just lurk if I need a fix to help keep the clutter down but this problem is really irritating me and I cannot seem to find a fix.

How do I fix this? Also I'd like it if I didn't have to run xargs all the time, as this problem of too many arguments is just silly and there has to be a fix other than xargs.

Thanks in advance.

---

### Post by PaulFr on 2007-07-06
What about ```
mv ~/.Trash ~/.t && mkdir ~/.Trash && chmod 700 ~/.Trash && wipe -r ~/.t
```

---

### Post by vxbinaca on 2007-07-06
That works, thanks that's very inventive, i like it. Though I modified it slightly. I suplimented the above "wipe -r" with "wipe -c -r -f -i -S -r -P 200 -T 10" which is more secure.

An even better question then my last one:

Why limit argument length at all?

---

