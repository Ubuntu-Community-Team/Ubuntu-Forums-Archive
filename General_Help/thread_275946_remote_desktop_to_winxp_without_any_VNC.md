---
title: "remote desktop to winxp without any VNC"
date: 2006-10-12
forum: General Help
---

### Post by jagdishrao on 2006-10-12
hellow experts

i recently switched to ubuntu dapper (GNOME) as my desktop.
earlier i was using windows xp professional to connect to machines in US
using windows inbuilt Remote Desktop Connection feature.
as both were winxp machine i used to get superb performance.

now i am on ubuntu desktop  and i want to connect to Winxp prof 
machines in US using some software on ubuntu.
i cannot install any VNC server software there in US machines 
as it is a highly protected machine.

is it possible on ubuntu.
i tried using rdesktop but failed

rdesktop -u user 123.345.567.789:3389
ERROR: recv: Connection reset by peer

please help
jags

---

### Post by Sirkent on 2006-10-12
As far as I know, rdesktop is the only application that can do this. 

Try:
rdesktop 123.345.567.789

---

### Post by jagdishrao on 2006-10-13
> **Sirkent said:**
> As far as I know, rdesktop is the only application that can do this. 

Try:
rdesktop 123.345.567.789

hi sirkent yes it works
actually i was proving wrong ip to command
but also there is a tool called gnome-rdp which is agui for rdesktop
command line tool which manages the various connections and pwds

---

