---
title: "[SOLVED] Server Setup clarification questions"
date: 2008-06-25
forum: General Help
---

### Post by newbie_andy on 2008-06-25
I have a few questions on Ubuntu Server setup that I hope someone can help me with as some things are not working as they should.  My email does not work.  I followed "perfect setup" instructions from HowtoForge.com.

5 assumptions: 
a. I purchased abcd.com domain name and want to use it
b. I have a static IP 75.145.xxx.xxx
c. My server is on static ip 10.1.10.100 and PC on 10.1.10.101
d. In the end, I would like to host multiple domains and have a mail server (and DNS server if possible)

Problem:
1. When I try to access my website from PC, I get my router's login page.
2. My squirrelmail does not send out emails.

My Questions:
1. Is my hosts file set up correctly?

In /etc/hosts file, I have:
127.0.0.1       localhost.localdomain localhost
10.1.10.100     server.abcd.com  server

2. What records do I have to change with my registrar for abcd.com to point to my server?  (I changed the A and pointed it to 75.145.xxx.xxxx)

3. Is the name of my mailserver the same as above, server.abcd.com?

4. How do I configure the mx records so I receive mail and am able to send out mail?

5. If I buy another domain name, how do I make sure that it is being routed to my server?

6. Is my network interfaces set up correctly?
# The primary network interface
auto eth1
iface eth1 inet static
address 10.1.10.100
netmask 255.255.255.0
network 10.1.10.0
broadcast 10.1.10.255
gateway 10.1.10.1

7. Do I need to have two physical servers to utilize DNS Manager in ISPConfig?  If not, how do I get two hosts with different IPs?  

Sorry, I know it's a lot of questions.  I tried to figure a lot of them out myself with no success.  Thanks.

---

