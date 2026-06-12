---
title: "[SOLVED] Apache 2.2 question"
date: 2007-11-20
forum: General Help
---

### Post by twiceasworn on 2007-11-20
Ok, so I am running Apache 2.2 on a bunch of FreeBSD boxes here at work.  Currently we have vhosts set up and everything works wonderfully.  However, if you input the ip address of the machine into a browser it comes up with the "It Works" page.  I have tried to get the ip to be redirected to the domain name so that if you put in the IP it would bring up the actual website, however to no avail.  I figured I would just need to create another vhost entry specifying the ip address with a redirect rule to the domain, though this did not work.  Any ideas or comments would be greatly appreciated.

---

### Post by reckless2k2 on 2007-11-20
if you are accepting all incoming on one server but need the requests handled/directed to another server then you have to use mod_proxy and a vhost edit that points to the other IP/box. 

is that what you mean? if so i can give you a sample vhost edit.

---

### Post by twiceasworn on 2007-11-20
Well sort of.  Basically we have a Cisco CSS that handles the requests and divvies them out to the webservers.  I just want the ip address of the boxes to not go to the "It Works" page defaulted by apache and rather go to the website that the server is hosting.  so if you typed in the ip in the browser it would just bring up the website itself, not the "It Works" page.

---

### Post by mahousaru on 2007-11-20
If you are using namevirtualhost, try specifying ipaddress:80 instead of *:80 in the namevituralhost setting.

---

### Post by twiceasworn on 2007-11-20
I did.  In fact I tried every virtual host setting I could think of.  I think we have just decided to put some redirect code into the page itself that will redirect to website.  Thank you guys for your input and responses though!

---

