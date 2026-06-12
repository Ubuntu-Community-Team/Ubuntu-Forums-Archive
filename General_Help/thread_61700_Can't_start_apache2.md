---
title: "Can't start apache2"
date: 2005-09-01
forum: General Help
---

### Post by maril on 2005-09-01
What does this mean? What could be occupying port 80?  is the port not enabled somehow?


root@kewir:/usr/share/apache2/config # sudo apache2
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by arnieboy on 2005-09-01
[QUOTE=maril]What does this mean? What could be occupying port 80?  is the port not enabled somehow?


root@kewir:/usr/share/apache2/config # sudo apache2
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs[/QUOTE]
EDIT: 80 is the http port.

---

### Post by arnieboy on 2005-09-01
[QUOTE=maril]What does this mean? What could be occupying port 80?  is the port not enabled somehow?


root@kewir:/usr/share/apache2/config # sudo apache2
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs[/QUOTE]
This means that apache isn't shutting down completely before trying to restart. This means that the new process won't be able to bind to port 80 because it is still being used by the old copy of apache that wasn't completely shut down. 

remove all the old apache packages and install the fresh ones after a restart.

---

### Post by richburr on 2005-09-01
[QUOTE=arnieboy]80 is the port which browsers use to connect to the internet.[/QUOTE]

No, port 80 is not the port the web client uses, if that's what you mean, they use a high numbered port. They will generally connect to remote web severs which are running on port 80.

For example, here's my current connection, from the OSX netstat:

tcp4       0      0  172.16.31.5.50398      ubuntu.mirrors.t.http  ESTABLISHED

My web browser traffic is going out on port 50398, and hitting Ubuntu's web server on port 80.

You most likely have another web server already running on the box, which is using up port 80. It could be another copy of apache, like a different version. Have you checked the process list to see what's running? I'd look for apache/httpd stuff in the list.


Rich

---

### Post by arnieboy on 2005-09-01
[QUOTE=richburr]No, port 80 is not the port the web client uses, if that's what you mean, they use a high numbered port. They will generally connect to remote web severs which are running on port 80.

For example, here's my current connection, from the OSX netstat:

tcp4       0      0  172.16.31.5.50398      ubuntu.mirrors.t.http  ESTABLISHED

My web browser traffic is going out on port 50398, and hitting Ubuntu's web server on port 80.

You most likely have another web server already running on the box, which is using up port 80. It could be another copy of apache, like a different version. Have you checked the process list to see what's running? I'd look for apache/httpd stuff in the list.


Rich[/QUOTE]
port 80 is the http port. for an almost complete list of ports refer to this:
[http://www.computerhope.com/jargon/p/port.htm](http://www.computerhope.com/jargon/p/port.htm)

---

### Post by richburr on 2005-09-01
[QUOTE=arnieboy]port 80 is the http port. for an almost complete list of ports refer to this:
[http://www.computerhope.com/jargon/p/port.htm](http://www.computerhope.com/jargon/p/port.htm)[/QUOTE]

It is the HTTP port that web servers use, yes. That's different than the outgoing port that a web browser uses. Those are high numbered ports, like in the example I posted. The high numbered port on the client box connects to port 80 on the server box (assuming the server is using that default port).


Rich

---

