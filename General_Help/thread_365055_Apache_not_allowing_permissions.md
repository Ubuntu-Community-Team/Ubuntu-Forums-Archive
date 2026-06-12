---
title: "Apache not allowing permissions"
date: 2007-02-19
forum: General Help
---

### Post by Jon2D on 2007-02-19
Hello Folks,
Usually I just use the IRC channel but I have decided to try out the forums. I am having a problem with my webserver (apache with php4) I am trying to access files using 127.0.0.1 and when i navigate to that i get this error message:
> Forbidden

You don't have permission to access / on this server.
Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 127.0.0.1 Port 80

I am just using this computer to test my scripts but i did 
> sudo chown -R jon:jon /var/www 
to open the directory so i could browse and edit at my hearts content, thats pretty much all I have done so if anyone could shed some light I would really appreciate it.

-Jon

---

### Post by mcduck on 2007-02-19
> **Jon2D said:**
> 
I am just using this computer to test my scripts but i did 
```
sudo chown -R jon:jon /var/www
```
to open the directory so i could browse and edit at my hearts content, thats pretty much all I have done so if anyone could shed some light I would really appreciate it.


And there's your problem.. All files & directories outside your home have certain owners & rights for a reason, and they shouldn't be changed.

You'd bettter change that back, and from this on use 'sudo' to acess www files. For example you could press Alt-F2 and run 'gksudo nautilus' to open a file manager as root, allowing you to add & remove files in /var/www..

---

### Post by Jon2D on 2007-02-19
Is there not a way allow me to write/read those files without having to do alt+F2 gksudo nautilus?

---

### Post by mcduck on 2007-02-20
I suppose it could be possible to add your own user to 'www'-group or whatever the default user/group for /var/www is.

---

