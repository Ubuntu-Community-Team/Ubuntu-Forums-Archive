---
title: "VIA C3 800MHz"
date: 2006-08-25
forum: General Help
---

### Post by malius on 2006-08-25
I am curious if anyone has had any experience with Dapper and a Via C3 800MHz processor?  I want to put together a simple file server (Dapper Server) and the price and performace of this processor are inline with my needs.

Any thoughts, experience, and/or issues about this pairing are welcome!

---

### Post by az on 2006-08-25
I had a Via C3 733 Mhz box and it was dog slow on a desktop.  The C3 only has a small cache and is not very quick.

It is also a 386 class CPU, so don't use the server kernel, it can only run on a 686 or better.  Install using the alternate (or the desktop) cd, not the server cd.

It should be fine for a file server, though, it doesn't produce much heat, so the fan is quiet.  I think I read that you can even do away with the fan.

---

