---
title: "Cannot access moodle installation form another computer"
date: 2008-05-23
forum: General Help
---

### Post by furmat on 2008-05-23
Hello,

I have just installed Moodle 1.8.2 on Ubuntu 8.04

I can access Moodle from localhost but cannot access it from another computer. When searching for a solution to this problem, i read somewhere that this could be related to a Moodle installation program for Ubuntu. 

Would anybody know something about this. 

Thank you 

Furmat


- Sorry .. i found the problem

/etc/moodle/apache.conf 

uncomment 
#allow from all

---

### Post by dasmith on 2008-08-12
I too just installed Moodle.  Accessing from within the localhost works just fine.  If I try to access from outside the network, or other device on my network, it attempts to open the login from [http://localhost/moodle/login/index.php](http://localhost/moodle/login/index.php).  Is there any way to change the configuration to allow it accessible from outside the network?

---

### Post by cariboo on 2008-08-12
If it is web based, you will probably have to open port 80 on your router and I would advise setting a static ip address for the computer moodle is installed on. There are a lot of different routers available out thers so it is pretty hard to cover port forwaring on all of them. The simple answer is to forward port 80 from your computer to your router. To actually implement port forwarding on your router check the documentation that came on the install cd for your router. One thing to note is that some ISP's block port 80 to keep their customers from running servers.

Jim

---

### Post by dasmith on 2008-08-12
> **cariboo907 said:**
> If it is web based, you will probably have to open port 80 on your router and I would advise setting a static ip address for the computer moodle is installed on. There are a lot of different routers available out thers so it is pretty hard to cover port forwaring on all of them. The simple answer is to forward port 80 from your computer to your router. To actually implement port forwarding on your router check the documentation that came on the install cd for your router. One thing to note is that some ISP's block port 80 to keep their customers from running servers.

Jim
Thanks for responding cariboo907.

My machine is set with a static IP behind my router which I am using Smoothwall ver 3.0 Polar.  My wiki, blog, and home page all port forward just fine thru port 80.  I am also using Webmin thru port 10000 which is working just fine.

I figured the issue out, it was with my config.php file.  Since I installed from local machine, I had to tweak it so that it would brouse by the domain name instead of local host.  All is well.  Thanks for help.

---

