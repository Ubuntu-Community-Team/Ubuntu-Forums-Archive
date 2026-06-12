---
title: "Setting up test/development server"
date: 2014-10-14
forum: General Help
---

### Post by David_Sopczak on 2014-10-14
I would like to setup a test/development server for my current webpage. What would I need to do to setup a unused server as a test server for running new code before it goes to production?

---

### Post by TheFu on 2014-10-14
Do exactly what you did to setup the production server, just use a different IP and different domainname.

There are many different techniques and best practices depending on the sort of website, database, and language used. Best to ask those questions for each specific part.  

For example, the way I push code from test to prod for perl-Dancer apps is different than how I push code for ruby on rails apps.

---

### Post by SeijiSensei on 2014-10-14
For web development, I usually set up development shares on the same server as production.  I just use a separate directory tree for the development site, and use a different server name so I can set up a second virtual host.  For instance, if I have a site on [www.example.com](www.example.com), I'll create a dev.example.com entry in the DNS, then create a corresponding virtual host for that name whose DocumentRoot points to the development area.

---

### Post by David_Sopczak on 2014-10-14
Thanks for your help. I now have a better idea of what to do  for this project.

---

### Post by tgalati4 on 2014-10-14
Although this is a spare server, I would explore different virtual machine hypervisors.  Install one, then build 2 virtual machines that are identical to your production environment.  Do your development on one vm and "production" on the second.  Over time, switch the original server to your hypervisor machine--the one with the development and production vms.  Then take the original server, clean it up, add RAM, disks, whatever, and make another hypervisor and outfit it in a similar fashion.  That way you always have a production environment for rapid switchover as well as two identical development environments.

What are your High Availability requirements?  There are several ways to set up HA, depending on your services.  One example:  [http://askubuntu.com/questions/157472/how-to-replicate-2-ubuntu-server](http://askubuntu.com/questions/157472/how-to-replicate-2-ubuntu-server)

---

