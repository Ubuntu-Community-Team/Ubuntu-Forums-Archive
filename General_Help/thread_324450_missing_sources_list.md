---
title: "missing sources list?"
date: 2006-12-23
forum: General Help
---

### Post by DougieFresh4U on 2006-12-23
When I do: gksudo gedit /etc/apt/sources.list-from the terminal, it comes up blank. When I do: nano /etc/apt/sources.list- the sources list pops up. how can I put sources list backin gksudo gedit /etc/apt/sources.list? I was trying to install wine and I was trying to add a line to sources list and the nano way was not saving. Thanks for any help

---

### Post by meng on 2006-12-23
Most likely you mistyped the first (gksudo gedit) command, pointing to a non-existent file.
Otherwise use:
sudo nano (etc)

---

### Post by taurus on 2006-12-23
```
sudo nano -Bw /etc/apt/sources.list
```
When you are done, press <Ctrl> and x.  Then "y" and return...

```
sudo aptitude update
```

---

### Post by DougieFresh4U on 2006-12-23
Thank you both.   Problem with mix of both answers. Merry Christmas.

---

