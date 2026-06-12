---
title: "what happens when system/KDE starts?"
date: 2005-08-08
forum: General Help
---

### Post by Copter on 2005-08-08
hi!

yesterday i installed some nice superkaramba meeters so i could check behavior of my computer in no time. i saw this way more strange things when my KDE starts. 

1) 100% cpu usage after KDE start for about 2 minutes or so. even when i dont touch and run anything. top says it something like updatedb, that stoles most of my cpu, that (according to man) updates slocate's database (?). it reads something from _all_ my hard drives. do i really need this? i also wonder what other things like this run in the backgroung that i dont know about. how can i see / edit this _list_?

2) after about 4 minutes of doing nothing i see that i have transmitted about 26kb and recivied 6kb of data. maybe im paranoid but i used windos for too long and i dont like apps doing things i dont know about (like sending passwords, personal data or anything else)

i dont say that Ubuntu, which kicks win's ass anywhere and anytime, does some spying around here. i just would like to know what is happening _out there_ :D

thanks for help!

copter :]

---

### Post by Sam on 2005-08-08
1) No problem for updatedb. It allows you to use the wonderful command 'locate' to find a file in a wink. The first time it take some time to index all your files, but the next time it'll be faster.

2) I don't know which app could do that. Maybe you can find it with netstat. But don't be paranoid about spyware or app sending password ! If you don't install anything untrusted there is no need to worry.

---

