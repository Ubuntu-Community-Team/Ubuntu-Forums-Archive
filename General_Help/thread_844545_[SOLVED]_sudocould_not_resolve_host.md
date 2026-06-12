---
title: "[SOLVED] sudo:could not resolve host"
date: 2008-06-29
forum: General Help
---

### Post by shmoe010 on 2008-06-29
I am pretty new to linux, but I have managed to figure out through tutorials how to get everything working that I need to do (thankfully.) This, however, I can't figure out. I changed my hostname to something different because I didn't like what it was before, and have restarted and everything since then, but I've found that many of my programs are becoming unresponsive. Also, whenever I launch an application from the terminal using sudo, I get the error:

```
sudo: could not resolve host (hostname)
```

To be honest I'm not sure what that means, but it doesn't sound good!

I have tried changing it back to what it was before but it didn't help. I have internet access and network access still, and some of my apps still work (like firefox for instance.) But a lot of my gnome apps are bugging out on me and becoming unresponsive.

Any thoughts would be much appreciated!

---

### Post by drs305 on 2008-06-29
Your host file could be corrupted or incorrect.

First, what is your hostname? It should be the name you selected, normally the computer name (....@hostname).
```
hostname
```


```

cat /etc/hosts

```

If it looks like this, it's normal. The second line should match your hostname:
```

127.0.0.1	localhost
127.0.1.1	yourcomputername

```

If the first two lines look like this:
```

127.0.0.1	localhost
127.0.1.1	yourcomputername.somethingaddedhere

```

Then:
```

sudo cp /etc/hosts /etc/hosts-backup
gksudo gedit /etc/hosts

```
and make it look like the first example, with no .somethingaddedhere and your correct hostname

---

### Post by shmoe010 on 2008-06-29
That fixed it for me. Thanks! :)

---

