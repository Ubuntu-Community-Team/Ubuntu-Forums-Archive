---
title: "Can't run CGI files in apache2 HELP!"
date: 2008-01-03
forum: General Help
---

### Post by bryanosaurus on 2008-01-03
I have setup apache2 on Ubuntu and having problems running .cgi scripts. 
I have searched everywhere on the internet and I cannot find any solution to get it to work. 

I have perl installed correctly and I can run .pl scripts fine from the cgi-bin. But when I try to sun a simple .cgi hello world, I keep getting this error:

"The server encountered an internal error and was unable to complete your request.  Error message:
The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there was an error in a CGI script."

The Apache Tutorial told me to add this:

<Directory /home/*/public_html>
Options +ExecCGI
AddHandler cgi-script .cgi
</Directory>

but it still doesn't help. 


Also, since messing around with my apache2.conf , I've been getting weird errors when restarting the server.

bryanosaurus@bryanosaurus:/var$ apache2 -k restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:40
no listening sockets available, shutting down
Unable to open logs

Server still works fine when restarted though. 

Any help would be greatly appreciated!

---

