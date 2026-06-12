---
title: "closing tasks"
date: 2006-10-07
forum: General Help
---

### Post by bastupungen on 2006-10-07
Hello!
I am running ubuntu 6.06 as an server. I chose the desktop version because i want to be able to use azureus when i feel like it. But most of the time its just an game/ftp/apache2 server, that doesn't really need the GUI front-end.

So my question is this. How can I turn of the GUI in the desktop version and also alot of the tasks (according to TOP: Tasks: 108 total,   1 running, 107 sleeping,   0 stopped,   0 zombie) that seems to be running in the background. I know how I can start some kind of gui through the vncserver, which is enough for me.

Why I wan't to do this is because i get alot of lag-spikes in source dedicated server srcds_l.

I am happy for all answers I can get in this issue. 

Also one quick question. If I close vncserver after adding my torrents to azureus, will azureus still run then?

---

### Post by bastupungen on 2006-10-07
bump

---

### Post by 3rdalbum on 2006-10-08
System > Administration > Services. Uncheck "Graphical Login Manager" and the X server will immediately quit. This will quit all graphical programs too.

To view all processes from the terminal, do:

```
ps aux | less
```

This will list the IDs and names of the running processes, and you can scroll up and down the list with the arrow keys. When you know the ID of the process you want to kill, type:

```
kill processID
```

where *processID* is the ID number, e.g. kill 4192.

---

### Post by bastupungen on 2006-10-09
Ah, thank you!

I guess this will quit Azureus since it is an "graphical program"? Or can I have the program running in the background somehow?

---

