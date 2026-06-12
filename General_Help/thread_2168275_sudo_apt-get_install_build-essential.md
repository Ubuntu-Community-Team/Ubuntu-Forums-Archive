---
title: "sudo apt-get install build-essential"
date: 2013-08-17
forum: General Help
---

### Post by xboox2 on 2013-08-17
> xxhitmanttg@Hax0rz:~$ sudo apt-get install build-essential
[sudo] password for xxhitmanttg: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
xxhitmanttg@Hax0rz:~$
I get this error and cannot find out how to make it work, Please help me. :confused:

---

### Post by plucky on 2013-08-17
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Close all package managers (Synaptic,Software Centre) etc. and then run ```
sudo rm /var/lib/dpkg/lock
``` from a terminal and then run ```
sudo apt-get update
``` and see if you still get the same error.

Good Luck

---

### Post by xboox2 on 2013-08-17
> **plucky said:**
> Close all package managers (Synaptic,Software Centre) etc. and then run ```
sudo rm /var/lib/dpkg/lock
``` from a terminal and then run ```
sudo apt-get update
``` and see if you still get the same error.

Good Luck

Still getting error, but not the same.
> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/


---

### Post by ibjsb4 on 2013-08-17
Reboot then try it.

---

### Post by xboox2 on 2013-08-17
i think it worked, but some how this box comes up everytime i install something and i cannot click ok.
>                                                                                 
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  

---

### Post by steeldriver on 2013-08-17
^^^ iirc you need to use the TAB key to navigate to the 'OK' box - then press ENTER or SPACE to 'select' it

---

### Post by xboox2 on 2013-08-17
> **steeldriver said:**
> ^^^ iirc you need to use the TAB key to navigate to the 'OK' box - then press ENTER or SPACE to 'select' it

wow, really that easy :P

---

### Post by ibjsb4 on 2013-08-17
> **xboox2 said:**
> wow, really that easy :P

That question comes up often. :)

---

### Post by xboox2 on 2013-08-17
Thanks for helping guys :) helped alot!

---

