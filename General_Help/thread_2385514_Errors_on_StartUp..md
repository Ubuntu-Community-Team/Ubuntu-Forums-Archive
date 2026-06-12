---
title: "Errors on StartUp."
date: 2018-02-21
forum: General Help
---

### Post by kazakore on 2018-02-21
I have recently started to get two error message at StartUp saying a component of Ubuntu has failed. When clicking on Report I don't get the second window showing me any information about the error so I have no idea what it refers to. I've had a glance over dmesg and sys.log and neither has anything that jumps out at me. Could you please have a look and see if there is anything obvious that I should worry about/correct...

Screenshot.

[ATTACH=CONFIG]278607[/ATTACH]

dmesg:
[https://paste.ubuntu.com/p/gjswGx6vsc/](https://paste.ubuntu.com/p/gjswGx6vsc/)

sys.log:
[https://paste.ubuntu.com/p/BmdYV9P6Ys/](https://paste.ubuntu.com/p/BmdYV9P6Ys/)

---

### Post by cruzer001 on 2018-02-21
Could be a false positive.  You can reset it in terminal.

```
sudo rm /var/crash/*
```

If the report regenerates, then you do have a problem.

This is Apport
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

