---
title: "access tomcat7 webapp behind NAT"
date: 2016-04-26
forum: General Help
---

### Post by nos09 on 2016-04-26
Hello guys, 

I have been playing with [Guacamole]("http://guac-dev.org/"). 

I got it running on my VirtualBox vm with ubuntu. with apache configured to forward it to port 80, by default it runs on port 8080. Everything's works fine on the VM.

Then I wanted to deploy it on my digitalOcen machine. I installed all the dependacies. and then the tomcat7 and apache2 packages. After that if I access [http://IPofServer/](http://IPofServer/) i can access the apache page but If i try to access [http://IpofServer:8080](http://IpofServer:8080) it keeps waiting for the response. I just cant figure out what is wrong with it ! I have tried lthree times to do that.. after I install apache2 package the port 8080 is not accessable somehow ! I have the same configuration running and working on my local VM. 

Now, if I have my vm running behind NAT is there any way to get it accesaable over the internet ?!? And if somebody can help me with the digital ocean server problem.

And both vm and my cloud servers running on ubuntu 14.04.

---

### Post by dragonfly41 on 2016-04-26
I suggest that you install zenmap.

then launch GUI with command .. gksu zenmap

In Target: field insert your IPofServer .. then Scan.
Look for conflicts with port 8080 .. or other clues.

---

