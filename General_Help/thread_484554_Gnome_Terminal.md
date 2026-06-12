---
title: "Gnome Terminal"
date: 2007-06-25
forum: General Help
---

### Post by neko18 on 2007-06-25
Is it possible to make a launcher that opens a gnome-terminal to a certain directory?

I tried these, but neither worked:
```
gnome-terminal -x cd /home/david/Desktop/fw
```
```
gnome-terminal -e="cd /home/david/Desktop/fw"
```

---

### Post by raja on 2007-06-25
```
gnome-terminal --working-directory='/home/david/Desktop/fw'
```

---

### Post by neko18 on 2007-06-25
Thanks

---

