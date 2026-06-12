---
title: "[SOLVED] How to autostart a process as another user?"
date: 2008-02-13
forum: General Help
---

### Post by b0rka7a on 2008-02-13
I want my server to start automatically when my PC starts. I have 2 users - one for me, and one for the server. ("boris" is mine, "server" is for the server)
When I add "<command>" to /etc/rc.local, the server starts as root.
When I add "<command>" to home/boris/.kde/Autostart, the server starts as "boris".
I want the server to start as "server", because it don't have sudo privileges.

Note: the server is not using GUI, and I use the user "server" only in the terminal.

So is there a way I can do this ? 10x

---

### Post by Jussi Kukkonen on 2008-02-13
Many daemons do this, take a look at examples in /etc/init.d/. You'll probably want to use start-stop-daemon with option --user.

---

### Post by b0rka7a on 2008-02-13
I can't find any examles in /etc/init.d/
Can you help me more ? And how to set that "start-stop-daemon" ?

---

### Post by b0rka7a on 2008-02-13
SOLVED !!!
:lolflag:
 start-stop-daemon -c cs-server --exec /home/cs-server/hlds.sh --start
Thank you ;)

---

