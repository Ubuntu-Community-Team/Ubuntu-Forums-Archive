---
title: "upgrading kernel will break modules ?"
date: 2007-02-12
forum: General Help
---

### Post by nephish on 2007-02-12
lo there all,

i had to compile the zaptel kernel modules for asterisk to see my card. No problem.
now i have in my little update manager the notification that i should update my kernel from the ubuntu archives to fix a security hole, if i do this, will i have to recompile the zaptel kernel modules ?

thanks 

sk

---

### Post by energiya on 2007-02-13
yes. If you have compiled them for version 2.6.x.x and you are updating to 2.6.x.x-x or something like that you have to recompile.

---

### Post by nephish on 2007-02-13
ok, do these kernel upgrades happen often ?
sorry i am new to this, but i am weighing out the security advantage over the trouble of re-doing these drivers very often.
thanks for your help by the way.

---

### Post by energiya on 2007-02-13
> **nephish said:**
> ok, do these kernel upgrades happen often ?
sorry i am new to this, but i am weighing out the security advantage over the trouble of re-doing these drivers very often.
thanks for your help by the way.

well... if your computer is a server, security is very important, but for the desktop user, kernel updates aren't so important (as long as they aren't critical). For example, I'm using kernel 2.6.18.6 but the latest kernel is 2.6.20 ... and my PC still works (others still use the 2.4 kernel) :) You could probably update less often than kernels appear in the repositorys.

---

