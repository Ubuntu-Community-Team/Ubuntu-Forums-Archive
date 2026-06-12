---
title: "ZIP support"
date: 2007-03-16
forum: General Help
---

### Post by arst06d on 2007-03-16
Hi

I have the UBUNTU LAMP server, on which I run Webmin.  When I upload a zip file using webmin I get 

Successfully uploaded the following files : blah.zip, which could not be extracted : Missing command unzip

Can anyone please advise how to install/enable zip support on ubuntu server?

Thanks

---

### Post by louis_nichols on 2007-03-16
They are in the repos: ```
 sudo apt-get install zip unzip 
``` Assuming of course that you have the right repos enabled. For this, open the surces.list file for editing: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list
``` and uncomment all repos there.

---

### Post by arst06d on 2007-03-16
That did the trick.

Many thanks

---

