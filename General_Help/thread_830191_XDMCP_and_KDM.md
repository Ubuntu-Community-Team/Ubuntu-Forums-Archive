---
title: "XDMCP and KDM"
date: 2008-06-15
forum: General Help
---

### Post by Landreville on 2008-06-15
In the past i've successfully configured XDMCP and GDM to login to a server from a laptop terminal. 

Now I cant figure out how to do the same with KDM.

I've edited kdmrc and enabled xdmcp, specified port 177 and the Xaccess file location. 

I edited the Xaccess file to accept all connections.

There is no firewall between the server and the terminal.

When i try to connect from the terminal (using "X -query 192.168.1.1") it tries to start X and then fails. 

The output says it was reject from IP 192.168.1.1 (with 5 attempts) before exiting.

Anything i missed, has anyone else gotten XDMCP and KDM working successfully? (in all my searching i havent seen **any** successful attempts with kdm)

---

### Post by Rui Pais on 2008-06-19
Same here with GDM. Both Ubuntu and Xubuntu. 
On Hardy XDMCP don't seems to work :(

---

### Post by Rui Pais on 2008-07-02
Just an update of these.

I made it work by doing this:
[http://ubuntuforums.org/showpost.php?p=5281868&postcount=5](http://ubuntuforums.org/showpost.php?p=5281868&postcount=5)

---

