---
title: "I want my apache server to listen on a particular port and process connections"
date: 2008-01-23
forum: General Help
---

### Post by LinuxNoob#1 on 2008-01-23
So this question I believe is really nooby.  :)  Basically what I have done is setup a LAMP server on my localhost.  Also I have written a perl script which I use to listen for and handle requests on a particular socket.  So it works great when I simply run the script and the test script.

I want to know how I can set it up so the server listens for action on my socket (also I do not know an appropriate port) then shoot up the perl script when something occurs to handle it.  Could someone help me out please?

---

### Post by robertpostill on 2008-01-23
Hi,
I'm not entirely sure what you mean but I'll make a guess or two and we'll see how we go.  I think what you're saying is that you have Apache and Perl installed and you've made a perl CGI script for your apache install.  You want to change the port from the default (which is 80) presumably so you can test things without trashing the webserver while you're developing the perl script.

The most direct thing to do is edit the config.  Under /etc/apache2/sites-available you should find a file called 000-default.  This file is the config for apache.   If you edit this you edit everything so *caution* make a backup before fiddling with the file.  Inside the file you'll find a line that says LIsten 80.  That sets the apache port, so simply pick a port you prefer and off you go.

As an alternative try adding a VirtualHost to Apache.  That will allow you to have a play area and leave the main config unsullied.  Its a big topic so you should probably start at [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/).  Which is the official Apache documentation for virtualhosts.

---

### Post by LinuxNoob#1 on 2008-01-23
No let me try to explain what I am doing :)  port 80 is what the browser uses right?  

What I want to do is let that stay the way it is.  I want an external computer to connect to my server lets say at port 7070 (or a suitable one) and sent information over this socket using tcp.

#initiate the socket
my $sock = new IO::Socket::INET ( 
	PeerAddr => 'localhost', 
	PeerPort => '7070', 
	Proto => 'tcp', 
); 
print $sock $package."\n";
clost $sock;

I want my apache2 localhost to accept this request on port 7070 and do some processing?

---

### Post by KCPokes on 2008-01-23
Just off the bat you cannot have two processes bound to the same port.  Cant have a Perl process using 7070 and Apache listening on 7070.  Not even sure what you are attempting to accomplish, but far as I can see this is not the best way to go about it.

---

### Post by LinuxNoob#1 on 2008-01-23
If I have the perl program on my server and want to bound it to that port how do i get it to just always run in the background and process any clients which try to use this port?

---

