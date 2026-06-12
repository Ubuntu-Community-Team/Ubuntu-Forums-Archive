---
title: "Out of Diskspace"
date: 2007-06-09
forum: General Help
---

### Post by reginabally on 2007-06-09
I recently installed Kubuntu in Ubuntu Desktop Environment.  I've checked the diskspace left for System, it shows that I have 1.3 GB left.  But after I restart and boot into Kubuntu, the system gave me the message something like this: My login session are not longer than 10 seconds, this might caused by some installation error or out of diskspace.

What should I do?  I can't login into all the sessions and don't know what to do with the terminal (I don't know about linux commands...).

---

### Post by kevinmedina on 2007-06-10
You cannot login into *any* session? Or can you log into ubuntu and not kubuntu?

---

### Post by ecology2007 on 2007-06-10
press Alt+F2, try to login in the console and type 
>  sudo aptitude clean
sudo aptitude autoclean

That should give you enough space to login on next reboot.
You can reboot with this command.
> sudo shutdown -r now

---

### Post by reginabally on 2007-06-11
> **kevinmedina said:**
> You cannot login into *any* session? Or can you log into ubuntu and not kubuntu?

I can't login into *any* session except the terminal.

> **ecology2007 said:**
> press Alt+F2, try to login in the console and type 


That should give you enough space to login on next reboot.
You can reboot with this command.

Thank you very much for your valuable reply.

---

