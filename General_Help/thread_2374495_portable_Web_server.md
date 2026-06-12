---
title: "portable Web server"
date: 2017-10-16
forum: General Help
---

### Post by alain.roger on 2017-10-16
Hi,

i have several computers (laptop, desktops) and i work on each of them according to place where am I (At work, at home - in bedroom, in living room).

When i was using windows OS, I did a web server using portable versions od PHP, apache, xdebug, MySQL (for windows) and i was only synchronizing the webserver folder directly among those computers.

I'm not happy with the situation where under Linux, you have to install a xAMP stack on each computer to work. It means 1 new setting should be replicated on each of them and that's a waste of time for me.

I know i could use a 24h/24h webserver, but it would mean to upload each time database changes and php/javascript framework pages changes.

I would like to keep it as simple as that... to have a portable xAMP (with https + xdebug) stack e.g. in my /home/development/ directory but the location could change according to computer.

I tried Xampp, bitnami and so on, but ALL request ROOT access to start and to install.

Therefore i would like to know if someone already solved such situation and how ?

thanks

---

### Post by SeijiSensei on 2017-10-16
Make one computer a server with Apache, etc., and connect to it over the network from your other machines.

You'll need to use sudo to gain root on any such installation.

---

### Post by ian-weisser on 2017-10-16
> **alain.roger said:**
> I'm not happy with the situation where under Linux, you have to install a xAMP stack on each computer to work.

Then don't use that stack.
There are lots of ways to serve static and dynamic files.
Python, for example, will start a robust (though unsecure) static webserver using a single command.

---

