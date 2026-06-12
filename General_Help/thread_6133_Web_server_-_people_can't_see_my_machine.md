---
title: "Web server - people can't see my machine"
date: 2004-11-25
forum: General Help
---

### Post by jnetto on 2004-11-25
Hi folks,

i'm configuring a machine that has two ethernet interfaces, eth0 and eth1, one for my intranet and the other with a valid IP address that i want to be accessible by people outside, respectively.
These ethernet interfaces are both via-rhineIII and working properly... They are listed at the output of my ifconfig with they're respectively and correctly configured parameters.
The problem is that only people inside my intranet can ping this machine's ethernet interface eth1, that has the valid IP address. People outside this range, cannot.
I read that Ubuntu hasn't any daemons listening to the outside world, but i can't figure out how to do this and even if this has to do with my problem.
I would appreciate if anyone could help me on this thing.
Thanks.

---

### Post by Magneto on 2004-11-25
modify /etc/inetd.conf for your webserver -  Search the forums for apache setup information or google setting up apache on debian

---

### Post by jnetto on 2004-11-26
But, since i have the apache daemon already running and listening to the 80 port, i shouldn't have to specify it on the /etc/inetd.conf file.
My real problem is that people outside the range of my intranet cannot ping the ethernet interface eth1 (with the valid IP address), and consequently cannot access the page that i'm serving.
I've installed on the same machine, with the same IP address configurations, the Fedora Core 3 and it all worked well... People outside the range of my intranet were accessing my pages and pinging this machine...
But since i want to run it with Ubuntu Linux, i would like to figure out what is happening.

---

### Post by p!=f on 2004-11-26
What's the ethernet interface the webserver runs on?

---

### Post by jnetto on 2004-11-26
It's running on both ethernet interfaces...

---

### Post by Magneto on 2004-11-26
Hey sorry about that - its apache- 
im forgetting this is a multihomed system

you need to modify httpd.conf -  the Listen and BindAddress options have to be set correctly like so

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
#Listen 3000
#Listen 12.34.56.78:80

#
# BindAddress: You can support virtual hosts with this option. This directive
# is used to tell the server which IP address to listen to. It can either
# contain "*", an IP address, or a fully qualified Internet domain name.
# See also the <VirtualHost> and Listen directives.
#
#BindAddress *






Sorry about steering you wrong on that before

---

### Post by p!=f on 2004-11-26
[QUOTE=jnetto]It's running on both ethernet interfaces...[/QUOTE]
Ok. But what interface do you try to ping?
Do you have any firewall set up?
Do you have IP forwarding turn on?

---

### Post by jnetto on 2004-11-27
I'm trying to ping the eth1 interface, that has the valid IP address.
There's no firewall and no IP forwarding.

---

### Post by Magneto on 2004-11-27
[QUOTE=jnetto]I'm trying to ping the eth1 interface, that has the valid IP address.
There's no firewall and no IP forwarding.[/QUOTE]
 if you can't ping the interface but you know its up and you can ping things on that external facing network your ports are not open - I thought you already confirmed both interfaces were up and accessible

you have to check for three things

1. Your network interfaces are up and working

2. Your network interfaces are open to external requests for the right ports

3. Apache is configured to use both interfaces

---

