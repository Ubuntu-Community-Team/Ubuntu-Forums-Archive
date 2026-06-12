---
title: "Trouble setting up Apache on localhost"
date: 2008-07-01
forum: General Help
---

### Post by ceclauson on 2008-07-01
Hello!

I'm trying to get Apache to serve pages on localhost.  I'm completely new to this.  It was working a few, hours ago, and now it's not working anymore.

My understanding is this:
(1)localhost corresponds to the IP address 127.0.0.1
(2)localhost is actually your computer, so that you shouldn't have to be connected to the internet to either serve to it or download from it

My httpd.conf file contains the following directive:
```

Listen 127.0.0.1:80

```

When I try to run the server, this is what I get:
```

ceclauson@ceclauson-laptop:/usr/local/apache2/bin$ ./httpd
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

Again, I'm pretty new to this. Any help would be appreciated :-)

Cooper

---

### Post by iaculallad on 2008-07-01
Try running the command with **sudo**.

```
sudo
```

EDIT: 

```
sudo /usr/sbin/apache2ctl start
```

---

### Post by ceclauson on 2008-07-01
Nice! That's what I was doing before but not doing now.

Okay.  I've noticed another strange phenomenon.
(1) I can't use port 80, it only works when I use a port like 700 and
(2) If I use one port, reboot my machine, and then try to use it again, it won't let me.  If I use 800, and restart, I have to use 801 or something else  the next time.

Does anyone know why this is?

Thanks,
Cooper

EDIT

Here's the actual response if I try to use port 80:
```

ceclauson@ceclauson-laptop:/usr/local/apache2/bin$ sudo ./httpd
[sudo] password for ceclauson:
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```
Similar if I use 800 after having already used it:
```

ceclauson@ceclauson-laptop:/usr/local/apache2/bin$ sudo ./httpd
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:800
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by iaculallad on 2008-07-01
Try to check for Apache's ports.conf file and delete multi listen entries to same ports.

First location:

```
gksudo gedit /etc/apache2/ports.conf
```

Second location:

```
gksudo gedit /etc/apache2/sites-enabled/ports.conf
```

---

### Post by ceclauson on 2008-07-03
Okay, apparently that file already tells my server to listen to port 80, so that's why when I added a Listen 80 directive to the other file, I got an error message.  Also, [http://localhost:80](http://localhost:80) gets a response, so apparently it all works.

Strangely, the Apache seems to be serving files from a different location on port 80 than on port 700.  I'm still really confused about this, but at least it seems to work, and I'll probably get it figured out with a bit of tinkering.

Thanks again so much.

Cooper

---

