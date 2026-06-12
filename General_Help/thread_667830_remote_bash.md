---
title: "remote bash?"
date: 2008-01-14
forum: General Help
---

### Post by AWerner32 on 2008-01-14
i have a desktop and a laptop both of which i've used for ages and i would consider myself pretty saavy, but i've found something i'd like to do that i cant figure out. say i want to be running a process on the desktop but have the bash output be repeated on a laptop shell. I dont want to ssh in because then when the connection is severed the process is halted but i would like to see the remote output locally of a remote process. Is that possible with by any means. I'm not talking about through X or anything either the desktop is solely a server.

---

### Post by geirha on 2008-01-14
If you log in with ssh, start [screen]("http://www.kuro5hin.org/story/2004/3/9/16838/14935"), then run the process inside that screen, then you can watch it on both computers simultaniously, and if the ssh-connection is severed, the process will still be running, and you can simply log back in and resume the screen.

---

### Post by HermanAB on 2008-01-14
You could simply open another terminal and log in with ssh again.  You can have as many ssh sessions as you need.  Some people prefer using screen, but I have never bothered with it.

Cheers,

Herman

---

