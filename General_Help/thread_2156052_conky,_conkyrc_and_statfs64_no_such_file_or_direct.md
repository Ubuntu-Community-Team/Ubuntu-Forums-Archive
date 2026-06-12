---
title: "conky, conkyrc and statfs64 no such file or directory"
date: 2013-06-20
forum: General Help
---

### Post by creepwood on 2013-06-20
I started using conky a while ago but I never finished it and now my use has changed to something else. However, when I start conky I get an error:

```
Conky: statfs64 '/media/data': No such file or directory
```

Well this is true, but I removed those instances on the conkyrc file, saved the file and restarted conky. However, I'm still getting the same error. I used the command

```
killall -SIGUSR1 conky
```

to restart conky. I'm somewhat of a newb when it comes to ubuntu and it's file structures, etc.

Is there anywhere else it reads config from?

---

### Post by creepwood on 2013-06-20
Solved, but I don't know why. I've been fiddling with the rc file, layout and stuff and it just disappeared along the way.

---

