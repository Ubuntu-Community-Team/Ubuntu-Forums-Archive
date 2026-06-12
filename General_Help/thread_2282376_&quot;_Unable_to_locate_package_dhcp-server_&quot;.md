---
title: "&quot; Unable to locate package dhcp-server &quot; while trying to apt-get install dhcp-server"
date: 2015-06-13
forum: General Help
---

### Post by marnikbruyndonckx on 2015-06-13
Hello, I've been searching the internet now for a while and I couldn't really find a clear answer.

Normally this should display when NOT having an internet connection, but I DO have one. So that's where the problem is..

It's pretty simple, trying to install the dhcp-server using " apt-get install dhcp-server " but I get the error " Unable to locate package dhcp-server ". 

I do run the command in root, so this could not be the problem. I checked my internet connection by pinging to 8.8.8.8 (google dns servers) with result.

Did I perhaps misspelled something? This should be a pretty basic command, I'm just looking over something.. :/

Looking forward to hear from this forum, I just made an account to get this problem fixed.

Thanks in advance!

---

### Post by steeldriver on 2015-06-13
Hello and welcome to the forums

What is your Ubuntu version? AFAIK the DHCP server is provided by virtual package dhcp**3**-server (which resolves to package isc-dhcp-server, at least in currently-supported versions)

---

### Post by papibe on 2015-06-13
> **steeldriver said:**
> isc-dhcp-server
+1

The packages changed names (some time ago). This are the names of the common DHCP related packages:
```
isc-dhcp-client
isc-dhcp-common
isc-dhcp-server
```
Here is an Ubuntu tutorial: [isc-dhcp-server]("https://help.ubuntu.com/community/isc-dhcp-server").

Regards.

BTW: here's the old documentation [dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server"). Second paragraph explains it is obsolete, and points to the other help page.

---

### Post by sandyd on 2015-06-13
Helpful hint: if you know the approximate name of the program, you can use the following command
```

apt-cache search *packagename*
```

For example:
```

apt-cache search dhcp-server
isc-dhcp-server - ISC DHCP server for automatic IP address assignment
isc-dhcp-server-dbg - ISC DHCP server for automatic IP address assignment (server debug)
isc-dhcp-server-ldap - DHCP server that uses LDAP as its backend
tcos-configurator - PyGTK tool to configure some needed services to get a TCOS server
```

---

### Post by marnikbruyndonckx on 2015-06-14
Hello, thanks for all the comments and help.

After using the command [COLOR=#000000][FONT=Ubuntu Mono]apt-cache search dhcp-server, I get:
[/FONT][/COLOR]isc-dhcp-server - ISC DHCP server for automatic IP address assignment
isc-dhcp-server-dbg - ISC DHCP server for automatic IP address assignment (server debug)
isc-dhcp-server-ldap - DHCP server that uses LDAP as its backend

So this seems right, I guess?

Next, I tried " apt-get install isc-dhcp-server " which resulted in " E: Invalid operation isc-dhcp-server ".

---

### Post by steeldriver on 2015-06-14
... are you sure you didn't miss out the word [FONT=courier new]install[/FONT] from the command?

```

sudo apt-get install isc-dhcp-server

```

---

### Post by gtr@frii.com on 2015-09-27
I am currently unable to install the dhcp server
```

glensa@agplatter:~$ sudo apt-get install isc-dhcp-server
Reading package lists ... Done
E: Unable to locate package isc-dhcp-server
glensa@agplatter:~$ sudo -i
root@agplatteer:~# apt-get install isc-dhcp*
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Note, selecting 'isc-dhcp-client' for regex 'isc-dhcp*'
Note, selecting 'isc-dhcp-common' for regex 'isc-dhcp*'
isc-dhcp-common is already the newest version
isc-dhcp-client is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
root@agplatter:~#

```

This is on a fresh install (one day ago) of 14.04.3 LTS  (i686)
I am attempting to get this running with i686 because the last version of x64 that boots on my server is -61-generic

---

### Post by ian-weisser on 2015-09-27
Er, please don't tack on to old threads. It's better to open a new thread for a new problem. 
Your symptoms may seem similar, but the cause may be quite different.

Well, you have shown that 'sudo' is not the problem.
Do you have network connectivity?
Do your sources in /etc/apt/sources.list* files show the proper mirror?
You said this is a fresh install - did you create the dpkg database by running **sudo apt-get update**?

---

### Post by gtr@frii.com on 2015-09-27
Gads!  error 299. I did not update/upgrade after installation.  I was troubleshooting another problem on the hardware (wouldn't boot x64 kernels past -61-generic).  I installed14.04.3 LTS i686 server on this disk to see if it would boot a late i686 kernel.  It did, and I went back to troubleshooting the x64 problem - with no luck and/or advice.  So, I came back to this disk to try and get my home server back up running an i686 kernel and forgot that I had not done an update/upgrade after installation.  Did that and installed disc-dhcp-server successfully.  Now, I just need to get dns, samba, and nfs back up and I'll stay on i686 from here on out.  Aside - I will start new threads in the future.  Thanks for your help.

---

