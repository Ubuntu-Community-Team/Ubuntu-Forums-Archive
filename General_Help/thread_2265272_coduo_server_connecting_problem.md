---
title: "coduo server connecting problem"
date: 2015-02-13
forum: General Help
---

### Post by lauda on 2015-02-13
Hello. I installed an coduo linux dedicated server and run it perfectly but i have problem when i want to join server i get error message "EXE_TIMEOUT". I tried with server config but problem is still here. I use Ubuntu 14.04 LTS Desktop i386 how to fix this prob?

---

### Post by lauda on 2015-02-14
i think this is problem with sshd_config but i dont have it in /etc/ssh  directory i have just ssh_config. what i need to edit there to fix  problem with connecting to my coduo server?

[IMG]http://www.burebaruta.tk.hostinghood.com/coduobots/Screenshot%20from%202015-02-14%2017%2038%2004_1.jpg[/IMG]

---

### Post by lauda on 2015-02-16
I've solved this problem so I changed the setting sv_timeout "9999999999" to be sv_timeout "300" and now I have no problem to connect to the server.

---

