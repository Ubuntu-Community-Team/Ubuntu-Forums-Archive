---
title: "Stopping X"
date: 2006-10-18
forum: General Help
---

### Post by DesignerX on 2006-10-18
How do I stop X.org and restart it ?

thx.

---

### Post by taurus on 2006-10-18
```

<Ctrl><Alt>Backspace

```

---

### Post by DesignerX on 2006-10-18
thx, and how do I restart it ?

I know there is a command line for stopping and starting services, what is it ?

---

### Post by taurus on 2006-10-18
That command should restart X for you!  You mean it kicked you out to a console right now!  What happens when you press <Ctrl><Atl>F7?  Otherwise, try

```
sudo /etc/init.d/gdm start
```

---

### Post by DesignerX on 2006-10-19
thx man.

---

