---
title: "kde programs start error, related to dcopserver"
date: 2007-05-06
forum: General Help
---

### Post by baosheng on 2007-05-06
Hi,

I found a common problem when I wanna start KDE programs, such as Kile or Quanta. 

If I start them as a common user, without sudo, it will pop-up a new windows like the attachment. It says:
[INDENT]There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/forrest/.DCOPserver_flavia_1

Please check that the "dcopserver" program is running![/INDENT]

After I click OK on this window and later few windows, the program is terminated.

But if I start them as superuser, it seems ok.

How can I fix this problem? What is the DCOPserver?

Thanks.

---

### Post by hackbox on 2007-05-09
Same kind of problem here with AcetoneISO on Feisty.

---

### Post by hackbox on 2007-05-09
been able to run Acetoneiso within a terminal with "sudo acetoneiso".  no error message.  Don't know if it can help with other apps. Good luck

---

### Post by baosheng on 2007-05-10
but why I have to sudo? I think there is no such need.

---

### Post by baosheng on 2007-05-11
I know what to do now.
I run a "sudo chmod 0777 ~/.kde -R" and everything is OK.

---

### Post by gekkos on 2008-05-24
Just check who owns ~/.kde, if it is not you than change ownership to your username. 
sudo chown yourusername:yourusername .kde
sudo chmod -R 0750 ~/.kde (don't make it world read/write/executable)

---

