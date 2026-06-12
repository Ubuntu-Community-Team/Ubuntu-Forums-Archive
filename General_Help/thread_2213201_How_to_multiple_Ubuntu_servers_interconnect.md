---
title: "How to multiple Ubuntu servers interconnect?"
date: 2014-03-25
forum: General Help
---

### Post by ELMIT on 2014-03-25
I got 3 servers (A, B, C), each one has two Ethernet cards, eth0 towards the wild and dangerous Internet, and eth1 to the internal lan (10.0.0.x)

Server A has a mysql database which should be reachable from the Internal Lan (eth1 any of 10.0.0.x). And from ONE and ONLY ONE public IP address via eth0.
This one remote IP address runs some program and needs access to the database. The same remote IP should also use phpmyadmin to connect to that database.

How can I set it up?

---

### Post by TheFu on 2014-03-25
Yes you can, but it is a bad idea to access mysql over non-encrypted channels over the internet. passwords would be in cleartext - not good.

Use a VPN or ssh tunnels - then you don't need ANY public facing mysql on the internet, which is extremely dangerous.

---

### Post by ELMIT on 2014-03-25
How do I do that? What packages do I need, is there a tutorial for doing that?

---

### Post by bab1 on 2014-03-25
> **ELMIT said:**
> How do I do that? What packages do I need, is there a tutorial for doing that?

Are these 3 computers in the same physical location?  Describe the network you have a little more.

---

### Post by ELMIT on 2014-03-26
The servers A, B and C are Cloud servers with public IP and an internal IP. I would not trust the Internal IP either, since I believe that other customers on the cloud could get to the port (maybe).
Currently the servers A, B and C have their own database server, and we plan to move them out into a dedicated mysql server in the cloud (will be server E)

I have a testing server (X)  at my location, which needs to connect to the database server (of A, B, C and later E). I can better debug and test, and still use real data for that.


I like the idea of VPN, but have never setup one. I have also no idea how it would work from X to A, B, C and later D. I also need to maintain the database and do that often with phpmyadmin. Unfortunately I could not install phpmyadmin on a Tomcat server (here C).

---

### Post by bab1 on 2014-03-26
> **ELMIT said:**
> The servers A, B and C are Cloud servers with public IP and an internal IP. I would not trust the Internal IP either, since I believe that other customers on the cloud could get to the port (maybe).
Currently the servers A, B and C have their own database server, and we plan to move them out into a dedicated mysql server in the cloud (will be server E)

I have a testing server (X)  at my location, which needs to connect to the database server (of A, B, C and later E). I can better debug and test, and still use real data for that.


I like the idea of VPN, but have never setup one. I have also no idea how it would work from X to A, B, C and later D. I also need to maintain the database and do that often with phpmyadmin. Unfortunately I could not install phpmyadmin on a Tomcat server (here C).

If you have no trust then everything needs to be encrypted via either ssh as a singular connection/app (i.e secure terminal or SFTP) or via encrypted tunnels via OpenVPN or some such.  The idea is that only the endpoints can decrypt the data.  You may need to script the data transfer too.  Lot's of work to do on this project.  There is no simple answer to your needs.

I would start with  [OpenVPN]("https://www.google.com/search?q=OpenSSH+tutorial&btnG=Go!#q=OpenVPN+tutorial+%2Bubuntu+-chroot") info and [OpenSSH/SFTP]("https://www.google.com/search?q=OpenSSH+tutorial&btnG=Go!#q=OpenSSH+sftp++tutorial+%2Bubuntu+-chroot") info.

---

### Post by TheFu on 2014-03-26
> **bab1 said:**
> If you have no trust then everything needs to be encrypted via either ssh as a singular connection/app (i.e secure terminal or SFTP) or via encrypted tunnels via OpenVPN or some such.  The idea is that only the endpoints can decrypt the data.  You may need to script the data transfer too.  Lot's of work to do on this project.  There is no simple answer to your needs.

I would start with  [OpenVPN]("https://www.google.com/search?q=OpenSSH+tutorial&btnG=Go!#q=OpenVPN+tutorial+%2Bubuntu+-chroot") info and [OpenSSH/SFTP]("https://www.google.com/search?q=OpenSSH+tutorial&btnG=Go!#q=OpenSSH+sftp++tutorial+%2Bubuntu+-chroot") info.

Exactly. Also, does your home connection have a static IP that will NEVER change according to the contract?  It can be dangerous to only open 1 IP for external use, so there are other tools that dynamically firewall IPs with failed login attempts - fail2ban is one and works with ssh. Always use ssh-keys, never password logins.

---

