---
title: "[SOLVED] how to run commands at shut down"
date: 2007-09-11
forum: General Help
---

### Post by minal on 2007-09-11
Hi,

As we can enter commands in /etc/rc.local so that they are executed on boot time , can we do same while shutting down system?

I want to execute some commands before shut down. Can i do that?

If yes, then how??

thanx for the help...

---

### Post by bmorency on 2007-09-11
if you put them in /etc/rc6.d they should get run when you shutdown. run level 6 is for shutdown.

---

### Post by minal on 2007-09-12
Hi,

thanx for the reply.. i tried dat.. but i guess run leve 6 is for restart. so i added it in rc0.d 

thanx again..

---

