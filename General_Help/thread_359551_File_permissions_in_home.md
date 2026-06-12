---
title: "File permissions in /home"
date: 2007-02-12
forum: General Help
---

### Post by PetePete on 2007-02-12
i've looked around the internet but got a bit confused so thought i'd ask here!

i want my /home/user directories to be private , currently its setup so that any user can view the files in another users directories.

ok so i do chmod 660 /home/user 

but then a user creates  a file in their home and its setup with the permissions o+r

I read about the umask but thats a global thing and i'm worried it will mess up other permissions elsewhere in the filesystem. 

so my question is, whats the easiest way to inherit permissions in ubuntu? so I can set a folder with 660 perms and anything created or placed into that also gets the perms 660 ?

(using CLI, (on server))

---

### Post by nereid on 2007-02-12
You could set the umask to 006 (if I'm correct, should be the complement of 660). So every non executable file will have the 660 permission.

Maybe [this](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html) could help you.

---

### Post by WW on 2007-02-12
I went all out--I use umask 077.  Anything that I want visible to groups or the world I adjust by hand.

If your server is a web server, and you have a web page stored in public_html in your home directory, 'chmod 660 /home/user' will not allow the web server to access your web page.  I left the permissions on /home/user at the default values (u=rwx, g=rx, o=rx).

---

