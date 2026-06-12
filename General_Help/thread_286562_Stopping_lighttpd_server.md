---
title: "Stopping lighttpd server?"
date: 2006-10-27
forum: General Help
---

### Post by chris.olsen on 2006-10-27
When the package manager tries to update the lighttpd server I get errors and it seems that it is having a hard time in shutting down the server.
I have looked on the lighttpd site and couldn't find anything on how to do this. Does anyone know how to?

Thanks

--------------
The following packages will be upgraded:
  lighttpd
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/296kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 145521 files and directories currently installed.)
Preparing to replace lighttpd 1.4.11-3ubuntu3 (using .../lighttpd_1.4.13~r1370-1ubuntu1_i386.deb) ...
 * Stopping web server lighttpd                                          [fail] 
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping web server lighttpd                                          [fail] 
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/lighttpd_1.4.13~r1370-1ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Starting web server lighttpd                                          [ ok ] 
Errors were encountered while processing:
 /var/cache/apt/archives/lighttpd_1.4.13~r1370-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Littleweseth on 2006-10-27
If you can't find the 'polite' way to do it; ps xal | grep light will tell you the PID of the process. Use sudo kill [PID] -9 to ungracefully kill it on the spot.

There's probably a nicer way to do it - I assume that man lighttpd had nothing on this? It may be something like /etc/init.d/lighttpd stop - you use a similar command to this to kill apache 'politely'.

---

### Post by chris.olsen on 2006-10-28
Thanks for the help.  The polite was a valid way of doing it, but it always failed.  I ended up (not for this reason alone) reinstalling dapper after the edgy fiasco :) So all is good now

---

