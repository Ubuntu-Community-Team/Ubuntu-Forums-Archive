---
title: "Getting Apache2 and JBoss working together"
date: 2007-04-17
forum: General Help
---

### Post by gzoller on 2007-04-17
Hello,

I've just installed Ubuntu 6.10 Server edition for use as an app server.  I have JBoss 4.2 and Apache2 installed.  Through a lot of forum-reading (including this one) I've also installed mod-jk.  My problem is that I don't think I have it configured right.  Apache and JBoss still work fine stand-alone but I don't see requests being forwarded to JBoss from Apache.

In /etc/apache2/apache.conf I added: Include conf/mod-jk.conf
I added a directory /etc/apache2/conf and put these files in there:

mod-jk.conf
```
# Load mod_jk module
# Specify the filename of the mod_jk lib
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so

# Where to find workers.properties
JkWorkersFile conf/workers.properties

# Where to put jk logs
JkLogFile /var/log/apache2/mod_jk.log

# Set the jk log level [debug/error/info]
JkLogLevel info

# Select the log format
JkLogStampFormat "[%a %b %d %H:%M:%S %Y]"

# JkOptions indicates to send SSK KEY SIZE
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories

# JkRequestLogFormat
JkRequestLogFormat "%w %V %T"

# Mount your applications
JkMount /application/* loadbalancer

# You can use external file for mount points.
# It will be checked for updates each 60 seconds.
# The format of the file is: /url=worker
# /examples/*=loadbalancer
JkMountFile conf/uriworkermap.properties

# Add shared memory.
# This directive is present with 1.2.10 and
# later versions of mod_jk, and is needed for
# for load balancing to work properly
JkShmFile logs/jk.shm

# Add jkstatus for managing runtime data
<Location /jkstatus/>
JkMount status
Order deny,allow
Deny from all
Allow from 127.0.0.1
</Location>

```

workers.properties
```
# Define list of workers that will be used
# for mapping requests
# The configuration directives are valid
# for the mod_jk version 1.2.18 and later
#
worker.list=loadbalancer,status

# Define Node1
# modify the host as your host IP or DNS name.
worker.node1.port=8009
worker.node1.host=10.100.1.240
worker.node1.type=ajp13
worker.node1.lbfactor=1
# worker.node1.connection_pool_size=10 (1)

# Load-balancing behaviour
worker.loadbalancer.type=lb
worker.loadbalancer.balance_workers=node1

# Status worker for managing load balancer
worker.status.type=status

```
(I know I don't need LB with 1 server but that's the config I found on a forum and I may want to use LB in the future, so I kept it.)

uriworkermap.properties
```
# Simple worker configuration file
#

# Mount the Servlet context to the ajp13 worker
/jmx-console=loadbalancer
/jmx-console/*=loadbalancer
/web-console=loadbalancer
/web-console/*=loadbalancer

```

So far I haven't made any changes to JBoss.

What am I missing to get the forwarding working?
Thanks in advance,
Greg

---

