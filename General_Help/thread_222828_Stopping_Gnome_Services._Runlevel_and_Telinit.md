---
title: "Stopping Gnome Services. Runlevel and Telinit"
date: 2006-07-25
forum: General Help
---

### Post by jordilin on 2006-07-25
In order to do a backup, I would like to do it from a virtual console by typiing Ctrl+Alt+F1. Once I'm in the virtual console I would like to stop all the gnome services. Is there a way to do it? Does it have something to do with runlevels? In this case, which runlevel I have to switch?

---

### Post by tty01 on 2006-07-25
bring it down to single user mode by typing in init 1.  this should bring you to terminal with "hostname" login.  dont type anything as system is switching to single user.  wait for a prompt saying "Give root password for maintenance".  Or something along the lines of that.  once logging in you can check your run level by typing who -r.  to bring the pretty desktop back up type init 3.  Hope i helped ;)

---

### Post by jordilin on 2006-07-26
> **tty01 said:**
> to bring the pretty desktop back up type init 3.  Hope i helped ;)
But, by default we are in init 5, aren't we? So, once we end with init 1 we should go back to init 5, shouldn't we?

---

### Post by tty01 on 2006-07-26
oops sorry you are right. it would be 2 or 5.  i come from unix background and just starting to give linux a try. :oops:

---

### Post by jordilin on 2006-07-26
So, we should go to init 2 to stop gnome services and then back to init 5, right?

---

### Post by tty01 on 2006-07-26
> So, we should go to init 2 to stop gnome services and then back to init 5, right?

actually 2 and 5 are the same in debian. and ubuntu is debian based. what you want is init 1.  then init 2 or 5.  1 brings you down to single user mode, like you wanted.

---

### Post by jordilin on 2006-07-26
Yes, going to init 1 stops the gnome services and the X :D 
Thanks a lot. One last question, what does it mean single user mode? If I understand it means that only one user can log into the system, right? or it means something else?

---

### Post by tty01 on 2006-07-26
> One last question, what does it mean single user mode? If I understand it means that only one user can log into the system, right? or it means something else?
correct. And that user is root.  a.k.a super user mode. This is normally to do maitnenance work.  I'm not sure if you know this but you can do a backup without going down to init 1.  *nix o/s can be backed up even while processes is running.  Take a look at this link.  It should be easier than what you are currently trying.
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/11/how-do-i-make-linux-filesystem-backup.php]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/11/how-do-i-make-linux-filesystem-backup.php")

---

### Post by jordilin on 2006-07-26
> **tty01 said:**
> correct. And that user is root.  a.k.a super user mode. This is normally to do maitnenance work.  I'm not sure if you know this but you can do a backup without going down to init 1.  *nix o/s can be backed up even while processes is running.  Take a look at this link.  It should be easier than what you are currently trying.
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/11/how-do-i-make-linux-filesystem-backup.php]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/11/how-do-i-make-linux-filesystem-backup.php")

thanks a lot, indeed. I wanted to go to init 1 because in order to backup your evolution mail, some gnome services must be stopped. Take a look here:
[https://help.ubuntu.com/community/MigrateEvolutionToNewComputer](https://help.ubuntu.com/community/MigrateEvolutionToNewComputer)
The link you have pointed out is nice, but after several posts and thinking about using different tools I will use rsync to do my backups. ;-)

---

### Post by felipe1982 on 2007-11-14
I come from opensuse, where a user (root) could type "telinit 3" to drop into non-X, networked, multi-user mode. In Feisty, I can't do this.

In opensuse, 'telinit 1' dropped networking, and entered single-user mode. In Debian (ubuntu) init 2 is the same as init 5? What runlevel is multi-user, networking, non-X?

---

