---
title: "[SOLVED] Disabled processes still starting on boot?"
date: 2007-05-30
forum: General Help
---

### Post by digitalbenji on 2007-05-30
Hi,
  I've tried both services-control and boot up  manager, and neither one of them seems to contain all the processes I see in the init.  I'd really like to stop Wacom, and MySQL when the PC is booted.  MySQL is in services-control, and I have it disabled, yet if I do a ps -e | grep mysql, I see mysqld and mysql_safe both running after startup.  Does anyone know what's up with this?  I'd like to disable a lot of services, without going crazy with init script editing.

Ideas?  Does anyone know of a thread that has answers? 

Thanks

---

### Post by ZiVvmO on 2007-05-30
i have a very similar issue.  i have processes starting up that i dont want starting up (but i dont know how to disable them...).  maybe we can get more attention (and ill bump this up in the process).

i will suggest one thing (keep in mind that i have been using linux for about a week now so this may be totally obvious).  have you looked in your /etc/RCx.d directory to make sure the offending processes are not linking with your runlevel?

---

### Post by digitalbenji on 2007-05-31
I'm almost certain that those processes are linked to my runlevel.  I just don't want to go into my /etc/RCx.d directory and start making changes manually.  In the past, like on Edgy, rcconf worked perfectly for this, properly reading all the processes linked there.  On Feisty however, there seems to be some kind of problem or something else going on.  Hopefully someone more knowledgeable than us can post and educate us on what to do.

Thanks

---

### Post by digitalbenji on 2007-06-01
bump

---

### Post by digitalbenji on 2007-06-04
I figured this out, somewhat.  I installed sysv-rc-conf and was able to disable printing and mysql for real, they were set to start at runlevel 2,3,4.  Still can't figure out how to entirely stop Wacom Setup, but mysql and hp are both done.  Yay!

---

