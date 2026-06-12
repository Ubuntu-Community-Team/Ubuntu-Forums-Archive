---
title: "How to translate this strace to an apparmor rule ?"
date: 2022-08-08
forum: General Help
---

### Post by vbgf3 on 2022-08-08
> strace: connect(78, {sa_family=AF_UNIX, sun_path="/run/user/1000/bus"}, 20) = 0

and this one: 

> strace: connect(81, {sa_family=AF_UNIX, sun_path="/run/user/1000/at-spi/bus"}, 27) = 0


I currently have the entire run directory open for read write: 

>   /run/**                  rw,

Which I know is wrong and allowing too much rights. But Chrome doesn't connect to the internet unless I have the entire run directory specified as rw.  The apparmor profile is working, but I need to refine the rights to the run directory. 

Thanks.

---

