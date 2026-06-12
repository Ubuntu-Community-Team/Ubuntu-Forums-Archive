---
title: "problem trying to configure wine"
date: 2008-05-04
forum: General Help
---

### Post by onesojourner on 2008-05-04
I am trying to run this to configure wine but it says I do not own the folder:

```
peter@desktop:~$ sudo wine winecfg
[sudo] password for peter: 
wine: /home/peter/.wine is not owned by you

```

here is a pic of my permissions for my wine folder:

[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/Screenshot.png[/IMG]

Does any one have any ideas why I am getting this error?

---

### Post by ptn107 on 2008-05-04
try this in a terminal:

```
sudo chown -R peter:peter /home/peter/.wine/
```

---

### Post by Grishka on 2008-05-04
yes. you should never run wine as root. it's not safe. you don't want windows programs doing everything they want with your linux system, do you?

---

### Post by onesojourner on 2008-05-04
That did not work:

```
peter@desktop:~$ sudo chown -R peter:peter /home/peter/.wine/
[sudo] password for peter: 
peter@desktop:~$ sudo wine winecfg
wine: /home/peter/.wine is not owned by you

```

---

### Post by ptn107 on 2008-05-04
Post the output of this from a terminal in your home folder:
```
ls -la | grep wine
```

It should be similar to (only with your username not mine):
```
drwxr-xr-x  4 phil phil 4096 2008-05-04 11:54 .wine
```

---

### Post by Bari on 2008-05-04
I.ve just installled wine and been playing with it to try and get things to work. after I installed it there was an entry on the applications menu - Wine this expanded to several options one of which was to configure wine.

---

### Post by onesojourner on 2008-05-04
```
peter@desktop:~$ ls -la | grep wine
drwxrwxrwx  4 peter peter    4096 2008-05-03 10:30 .wine

```

---

### Post by mc4man on 2008-05-04
Just run winecfg  (no sudo, no wine in command)

---

### Post by onesojourner on 2008-05-04
> **Bari said:**
> I.ve just installled wine and been playing with it to try and get things to work. after I installed it there was an entry on the applications menu - Wine this expanded to several options one of which was to configure wine.


sweet thanks. that got my program working.

---

