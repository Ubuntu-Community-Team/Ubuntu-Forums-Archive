---
title: "open tcp sockets after new installation"
date: 2007-03-18
forum: General Help
---

### Post by Cruz on 2007-03-18
Hello there,

I just installed a fresh Ubuntu Dapper. netstat tells me there are two high port tcp sockets open listening for connections from localhost. The port numbers are 48215 and 52816 right now, but they seem to change after every reboot. This came to my attention after every dapper I insalled so far and I would like to get to the bottom of it.

Does anyone know what they are there for and what processes opened those sockets? I'm unable to find this out because netstat -ltp doesn't show the PID (it's displayed only as a "-") and that's where my linux knowledge ends.

Thanks,
Cruz

---

### Post by inCursorated on 2007-03-18
do sudo netstat -tlp and u should be able to see the program name and PID

---

