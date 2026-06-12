---
title: "Big Tor Problem and Vidalia"
date: 2007-07-28
forum: General Help
---

### Post by C4U53 on 2007-07-28
Ok.. well I do have tor running and it's loading right or so it seems. so is privoxy. I've edited the config file for both properly. now if I use the Tor enable button I get this error on any site I try to go too

 503  	
This is Privoxy 3.0.6 on localhost (127.0.0.1), port 8118, enabled
Connect failed

Your request for [http://www.google.com/](http://www.google.com/) could not be fulfilled, because the connection to [www.google.com](www.google.com) (127.0.0.1) could not be established.

This is often a temporary failure, so you might just try again. 

also when I try to launch Vidalia I get this.. 

Error connecting to 127.0.0.1:9051 [Connection refused]

I don't have any 'known'. firewall running. is there a way to enable these ports or what do I need to do?. Perhaps there is a firewall running I'm not sure of that's default on ubuntu?

Using fiesty 7.04 btw..

---

### Post by C4U53 on 2007-07-28
Well I found the cheap fix.. I used wine emu and just downloaded the exe =/.. Would still like to know how to fix it in linux

---

### Post by Yoooder on 2007-08-02
I would guess you misconfigured privoxy.

below is a copy of my /etc/privoxy/config, it's basically the default, with logging disabled and with Tor's socks4a configured.

I would guess you put the socks4a line as the first line, if you read the default /etc/privoxy/config file you'll see a note that "user-manual..." has to be the first line

> 
user-manual /usr/share/doc/privoxy/user-manual
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile standard  # Internal purpose, recommended
actionsfile global    # Global default setting for all sites
actionsfile default   # Main actions file
actionsfile user      # User customizations
filterfile default.filter
#logfile logfile
debug   1    # show each GET/POST/CONNECT request
debug   4096 # Startup banner and warnings
debug   8192 # Errors - *we highly recommended enabling this*
listen-address  127.0.0.1:8118
toggle  1
enable-remote-toggle  0
enable-remote-http-toggle  1
enable-edit-actions 0
buffer-limit 4096
forwarded-connect-retries  0
forward-socks4a / 127.0.0.1:9050 .


---

