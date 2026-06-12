---
title: "delay when rebooting or halt"
date: 2012-11-12
forum: General Help
---

### Post by contremaitre on 2012-11-12
Hello,

It takes about 20 seconds for kubuntu to reboot or halt, and there is 10-15 seconds between the lines :
All processes ended within 1 seconds

and

Unmounting temporary filesystems.

Here is a screenshot of the halt sequence :
[IMG]http://www.celeos.eu/divers_seb/images/kubuntu_halt.png[/IMG]

---

### Post by contremaitre on 2012-11-13
anyone ?

---

### Post by contremaitre on 2012-11-24
up

---

### Post by contremaitre on 2012-12-10
up

---

### Post by rnerwein on 2012-12-10
> **contremaitre said:**
> Hello,

It takes about 20 seconds for kubuntu to reboot or halt, and there is 10-15 seconds between the lines :
All processes ended within 1 seconds

and

Unmounting temporary filesystems.

Here is a screenshot of the halt sequence :
[IMG]http://www.celeos.eu/divers_seb/images/kubuntu_halt.png[/IMG]
hi
have a look in  /etc/init.d/killall
i think then you will understand why.
on the other side - if this fair time is to long for you --> use the power switch (with all consequences :-)   )

---

### Post by contremaitre on 2012-12-11
/etc/init.d/killall : no such file or directory.
Did you mean /etc/init.d/killprocs ?

---

### Post by rnerwein on 2012-12-11
> **contremaitre said:**
> /etc/init.d/killall : no such file or directory.
Did you mean /etc/init.d/killprocs ?
hi
oh yes i mean killprocs (kill all is a comment in the scripts)
as i know first the system is sending a SIGTERM (15) to the processes. but some of the processes block the SIGTERM (e.g. database applications waiting for the childs to complete their jobs - syncing data etc.) this make sense. you can imagine what's happen to
a database when the jobs are unexpected interrupted ( not only db-processes ......)
cheers

---

### Post by contremaitre on 2012-12-13
As you can see in my screenshot :
"all processes ended within 1 second".

So the issue seems to be after that.

---

### Post by rnerwein on 2012-12-13
> **contremaitre said:**
> As you can see in my screenshot :
"all processes ended within 1 second".

So the issue seems to be after that.
hi
the after that i think is: /lib/lsb/init-functions
cheers

---

