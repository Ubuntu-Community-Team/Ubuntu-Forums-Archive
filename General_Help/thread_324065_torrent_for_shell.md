---
title: "torrent for shell"
date: 2006-12-23
forum: General Help
---

### Post by mitjab on 2006-12-23
I am using ctorrent and ltorrent. But when i close putty conecction is lost and torrenst stop downloading.

Is any program that will work even if i close putty?

thx

---

### Post by kd7swh on 2006-12-23
closing putty closes the ssh terminal you are starting the programs in. it isn't the torrent client it is your ssh tunnel. that being said you could try other ssh clients. I think auto-ssh will keep tunnels alive even after you exit the client.

good luck.

---

### Post by pandu.rs on 2006-12-23
when u quit putty a HUP signal will be sent to all the process invoked from that terminal. hence those processes may quit once u close putty.

there is a program called 'screen', which u can use.

for more info see 'man screen'

Here is a basic tutorial [http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen)

---

