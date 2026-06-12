---
title: "I Need Help Making a Shell Script..."
date: 2007-05-23
forum: General Help
---

### Post by pyro_xp2k on 2007-05-23
I'm trying to write a shell script to weed out dead links in my sources list.  I got it to work perfectly up to...

```
grep -e "^deb" /etc/apt/sources.list | awk '{ print $2 }' | sort | uniq
```

...but after I add...

```
| awk '{  cmd="if ! wget " $NF "; then; echo " $NF "; fi" }'
```

...after, I get no output -- nothing seems to happen at all.
What did I do wrong?

---

### Post by stylishpants on 2007-05-23
It's easier if you don't try to run the shell cmd inside of "awk".  

How about this?

```

grep -e "^deb" /etc/apt/sources.list | awk '{ print $2 }' | sort | uniq | while read s; do echo -n $s; if `wget -q $s`; then echo " is alive"; else echo " is dead"; fi; done

```

---

### Post by pyro_xp2k on 2007-05-23
It's perfect!  Thanks.

---

