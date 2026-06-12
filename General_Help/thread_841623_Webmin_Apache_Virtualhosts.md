---
title: "Webmin Apache Virtualhosts"
date: 2008-06-26
forum: General Help
---

### Post by GCoffee on 2008-06-26
After recently installing a server on my pc + webmin I was wondering something.. Whenever I create a virtual server for apache in webmin I go to say: [http://test.localhost/](http://test.localhost/) and get either page not found/error establishing connection, or my root homepage at localhost.

Can someone give me a solution to this problem?

Cheers,
Gcoffee.

---

### Post by bodselecta on 2008-06-26
I've never used webmin and I'm maybe asking something really obvious, but have you added the host to your /etc/hosts file?

---

### Post by GCoffee on 2008-06-26
I add the virtual server to the etc/hosts file and get the index page from /var/www/

heres a copy of my hosts file:

127.0.0.1	localhost
127.0.1.1	ben-desktop
127.0.2.1	test.localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I tried this to:

127.0.0.1	localhost
127.0.1.1	ben-desktop
127.0.0.1	test.localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Please help

Cheers,
Gcoffee.

---

### Post by GCoffee on 2008-06-27
bump

---

### Post by GCoffee on 2008-06-28
Come on people, can I have a bit of help here? bump bump bump

---

### Post by bodselecta on 2008-07-06
Did you ever get this sorted?

I don't use virtual interfaces so couldn't help.
One thought i had though, is it possibly just an apache config problem? 
I've just recently started using ubuntu and apache2 is setup a bit differently, does webmin handle enabling the site?
Is it a single httpd daemon or multiple?
Have you checked the access logs to see what host was receiving the traffic?
And if you're running a single daemon, shouldn't you be using IP (not named) hosts (using the ip address rather than the name in the virtual host directive) ?
Just a few thoughts.....

---

