---
title: "Cant connect to vmware mui 8333 or webmin 10000 ???"
date: 2007-03-16
forum: General Help
---

### Post by BodleyTunes on 2007-03-16
Hi all,

I successfully installed webmin 1.333 and the latest vmware on feisty the other day.

I was accessing the webmin interface and the vmware mui web interface quite happily, then after rebooting the next day, I cant for the life of me connect to any of the web interfaces anymore!

Cant connect to webmin or vmware, tried re-installing webmin and it says its started and to "connect on port 10000" but whenever I try to connect from a machine , it just says it cant connect to the server.

as far as I know there are no firewall that I have installed.

Also when I am on the server in question, if I try to telnet to 10000 or 8333 using 

open localhost 10000
or 
open localhost 8333

I still get nothing, 

Vmware is running though because I can access it from a remote vmware console running on an xp box.

Whats up! plz help!!  

My computer is nforce 4 mobo, could that be f*cking with things?  What I dont understand is why it was working one moment, and broke the next.  Maybe i did something but i cant think what.

:(

---

### Post by BodleyTunes on 2007-03-18
bump 

can neone help?

I tried reinstalling the whole server again, just installed webmin and I still cant get to the damn webpage!!

i can ping the server from anywhere but when I try to telnet to port 10000 it says "could not open connection to the host on port 10000"

Is there a built in firewall with feisty or something?

```
Selecting previously deselected package libauthen-pam-perl.
(Reading database ... 54888 files and directories currently installed.)
Unpacking libauthen-pam-perl (from .../libauthen-pam-perl_0.16-1_i386.deb) ...
Selecting previously deselected package libio-pty-perl.
Unpacking libio-pty-perl (from .../libio-pty-perl_1%3a1.05-2build1_i386.deb) ...
Selecting previously deselected package libmd5-perl.
Unpacking libmd5-perl (from .../libmd5-perl_2.03-1_all.deb) ...
Setting up libauthen-pam-perl (0.16-1) ...
Setting up libio-pty-perl (1.05-2build1) ...
Setting up libmd5-perl (2.03-1) ...
Setting up webmin (1.330) ...
Webmin install complete. You can now login to https://linuxhost1:10000/
as root with your root password, or as any user who can use sudo
to run commands as root.

```

and telnetting to the port in question ...

```
Microsoft Telnet> o linuxhost1 10000
Connecting To linuxhost1...Could not open connection to the host, on port 10000:
 Connect failed
Microsoft Telnet>
```

---

### Post by BodleyTunes on 2007-03-18
FIXED!

by installing the tar version.

Installing manually.

Bobs your uncle, it worked!

:)

---

