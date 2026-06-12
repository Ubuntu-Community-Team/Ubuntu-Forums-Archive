---
title: "Apache does not start"
date: 2007-08-14
forum: General Help
---

### Post by YSH on 2007-08-14
When i try to start apache it doesn't work, and gives me an error message:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

i already tried to start it from root, but it gives me the same error. How to solve?

---

### Post by woorzel on 2007-08-14
the first line you get is just a warning and can be ignored.
the second line is more worrying - looks like it cannot bind to the HTTP port. is there already another program using port 80 ?

try a netstat -alpnt | grep LISTEN
and see if there's something else bound to 0.0.0.0:80

if that's not it and root cannot bind to the port either, then maybe some kind of kernel security setting? do you see anything relevant in the output of the dmesg command?

---

### Post by az on 2007-08-14
On a desktop, skype uses port 80.  On a server, another likely possibility is that you have both apache and apache2 installed.

---

### Post by YSH on 2007-08-16
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5594/apache2       

only apache 2 there, but it really doesnt start/restart

---

### Post by airmertana on 2007-09-07
I have the same problem only with port 443.  I changed back to port 80 and than the apache2 worked, but then I tryed to add 443 and it cam back with the error message.  I then did a ps -A and found that apache2 is running also I ran netstat -alnpt which showed apache2  listening on port 443. I then killed the apache2 process with the kill command followed by the apache2 pid shown under the ps command. Then did the /etc/init.d/apache2 start and it worked.  So there must be a problem in the startup process.

---

