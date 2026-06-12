---
title: "Boot and shutdown issues in dapper"
date: 2007-02-14
forum: General Help
---

### Post by McLaughysSN on 2007-02-14
Hey guys, 

Recently my dapper partition has been acting a bit weird. On boot-up the following processes will fail.

Starting basic networking...
Configuring network interfaces...

once the "Starting portmap daemon..." passes, the boot process looks to freeze. I fix this by hitting ctrl+c twice .

When I try to shutdown, everything looks to be fine until the process "Stoping apache 2.0 web server..." after this the screen goes black with the following option

Ubuntu 6.06.1 LTS *name of my computer*

*name of my computer* login:

nothing can be done from this screen that i've tried.

Any ideas where to go from here?. I'm at a loss

Thanks!

---

### Post by howlin_walleye on 2007-02-14
Can you boot to recovery mode? 

Take a look in /etc/rc2.d and see what processes are starting after portmap. They'll be named S19zzzzz - they run in sequence during boot. Not all of them print messages, though, so its not necessarily the next one that is the problem. 

In recovery mode can you switch to runlevel 2? (i.e. type "init 2")?

Dan

---

### Post by McLaughysSN on 2007-02-19
Hey, thanks for the post.

I actually dont see the /etc/rc2.d file

---

### Post by McLaughysSN on 2007-02-20
Any Ideas

---

### Post by McLaughysSN on 2007-02-20
Ok, 

When i run recovery mode this is where it first stalls out

[17179588.658000] IPv6 over IPv4 Tunneling driver
FATAL: Module cman not found
   Warning unable to load cman kernel moduleFATAL: Module dlm not found
   Warning unable to load dlm kernel modulecman_tool: can't open /proc/cluster/status, cman not running
Starting cluster managercman_tool: can't open /proc/clsuter/status, cman not running


*Then i press ctrl+c and get the following (then it stalls again):


Starting lock_gulmd:/etc/cluster/cluster.conf was not detected
Starting global network block device server: No configured exports.
Starting global network block device client: Starting Cluster LVM Daemon


*I press ctrl+c a second time and the system comes to the following:

Give root password for maintenance
(or type Control-D to continue): 


*I enter the password and boots to root terminal as expected and hit ctrl+d and everything boots to the gui as normal. The OS works perfectly fine and runs as normal, including the networking. 

**Shutdown Problem**
When i shut down (this of course in recovery mode) I get the following:


Stopping apache 2.0 web server...                                                   [ OK ]
apache2: Could not determine the server's fullt qualified domain name, using 127.0.0.1 for Servername


*From here the system does nothing and I have to power down the laptop

---

### Post by McLaughysSN on 2007-02-21
No one?

---

### Post by McLaughysSN on 2007-03-18
Anything i can do to replaced those portions of the boot process to fresh code? I'm desperate at this point.

---

