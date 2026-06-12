---
title: "Renaming workstation"
date: 2007-05-19
forum: General Help
---

### Post by pangenium on 2007-05-19
hi
when installing Ubuntu, i made a spelling mistake giving the name if my computer -- i wrote 'untited' instead of 'untitled'
its not so important but is very annoying :)
does anyone knows how i can rename my workstation?
thanks for the answers

---

### Post by aroch1 on 2007-05-21
To rename your workstation for the current session use the command

```
sudo hostname NEWHOSTNAME
```

This method, however, will not make the new host name persistent over reboots.  To do so, use the command

```
sudo echo "NEWHOSTNAME" > /etc/hostname
```

then call

```
sudo /etc/init.d/hostname.sh
```

to make the change active

(Information fromhttp://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html)

---

### Post by pangenium on 2007-05-24
thanks aroch1

---

