---
title: "CGI Files not executing"
date: 2008-03-11
forum: General Help
---

### Post by S201 on 2008-03-11
Hi, I finally made the jump to getting rid of windows server 03 and moving to ubuntu. So I'm trying to get my website up and running again and everything is working fine except for a cgi file. When I go to access the cgi file from another computer (or even the localhost of the server) all I get is a blank white screen. Any ideas what would cause a cgi file to do this? Sorry I can't provide any more information. Thats about all I know.
I'm running ubuntu desktop 7.10 on a custom built machine and using the xampp for linux web server. Any help or a point in the right direction would be awesome. Thanks! :)

---

### Post by hyper_ch on 2008-03-11
look at the apache log and apache error log. That should give you some information.

---

### Post by S201 on 2008-03-11
It seems that this would be the problem...

[HTML]
...
[Tue Mar 11 06:20:34 2008] [error] [client 192.168.2.1] (2)No such file or directory: exec of '/opt/lampp/htdocs/proxy/nph-proxy1.cgi' failed
[Tue Mar 11 06:20:34 2008] [error] [client 192.168.2.1] (2)No such file or directory: exec of '/opt/lampp/htdocs/proxy/nph-proxy1.cgi' failed
[Tue Mar 11 06:20:34 2008] [error] [client 192.168.2.1] (2)No such file or directory: exec of '/opt/lampp/htdocs/proxy/nph-proxy1.cgi' failed
[Tue Mar 11 06:20:35 2008] [error] [client 192.168.2.1] (2)No such file or directory: exec of '/opt/lampp/htdocs/proxy/nph-proxy1.cgi' failed
...[/HTML]


I'm not understanding how it says there not a file there. That path and file are both correct. Or is that a file execution problem?

---

### Post by hyper_ch on 2008-03-11
I think you are not allowed to run the cgi in that folder - you would need to set in apache2.conf (or site configuration) that in this folder cgi are permitted to run... just my guess.

---

### Post by S201 on 2008-03-12
I got it all figured out. I'm not sure exactly what was wrong but I think it might have been something with the shebang line in my script not allowing the script to execute. Makes sense if that was the problem. Thanks! :)

---

### Post by fragos on 2008-03-13
The shebang provides the location of the correct script processor.

---

