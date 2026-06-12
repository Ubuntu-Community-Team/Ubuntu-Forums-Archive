---
title: "[SOLVED] Path not working (but &amp;quot;which&amp;quot; shows correct path)"
date: 2008-01-29
forum: General Help
---

### Post by jazzgossen on 2008-01-29
I made a script, and put it at a place in my path, but it wont execute, unless I call it with the full path. "which" finds the script, but it's not being called on the shell command line. What can be wrong?

```
~> which sbon
/home/martin/.programs/bin/sbon

~> sbon
sudo: sbon: command not found

```

---

### Post by espressopigeon on 2008-01-29
What's the output of ```
echo $PATH
```

---

### Post by jazzgossen on 2008-01-29
```
~> echo $PATH
.:./bin:/home/martin/.programs/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by espressopigeon on 2008-01-29
Why does it say
```
sudo: sbon: command not found
```
and not the standard
```
bash: sbon: command not found
```

Are you using the bash shell?

---

### Post by jazzgossen on 2008-01-29
No, I'm using dash, which is the default in Ubuntu 7.10. 

One thing I forgot to say is that there used to be another script called sbon at /usr/local/sbon, but I have deleted that and rebooted the computer.

---

### Post by jazzgossen on 2008-01-29
Sorry! I found the problem. I also had an alias called sbon that was causing trouble. Thanks a lot for your effort.

---

### Post by espressopigeon on 2008-01-29
Well, you had me baffled.

---

