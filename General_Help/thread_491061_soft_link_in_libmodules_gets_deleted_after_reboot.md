---
title: "soft link in /lib/modules gets deleted after reboot?"
date: 2007-07-03
forum: General Help
---

### Post by thinking on 2007-07-03
hiho@ll

i tried installing the fglrx driver for my ATI graphics card, which is working now but i have a little problem
to complete the driver installation i created a soft link
ln -s /lib/modules/2.6.20-16-generic/misc/fglrx.ko /lib/modules/2.6.20-16-generic/volatile/fglrx.ko
after modprobe and restarting X everything works fine
after rebooting the link has been removed!? and no driver is loaded cause it can't be loaded (cause soft link is missing)

1. why? does ubuntu create /lib snapshot's? if yes, how (i'm interessted in technical details, where is it stored, how long, ...)? and why?
2. how can i fix this? i'm sure there is a simple "sudo someupdatecommand" which i just don't know

thx@ll

---

### Post by thinking on 2008-03-21
just to make it a bit clear and "answer" myself
/lib/modules/.../volatile is tmpfs mounted ^^

lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)

---

