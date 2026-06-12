---
title: "&quot;NODE controller&quot; failed due to virtualiztion accleration!!"
date: 2014-08-10
forum: General Help
---

### Post by jayon on 2014-08-10
i installed the front end on the oracle VM ware!! successfull!
but next step in installing NODE controller! it showed me a error "this hardware does not support virtualization acceleration"
My question is that can i install NODE controller in one virtual machine! and front end in another virtual machine in the same OS?? sorry if it sounds like dump..
Newbie here! please help me ! :|

---

### Post by nerdtron on 2014-08-10
From my understanding, NODE controller means that it is the one that will host the VMs. That means that the NODE controller must be installed on a physical machine and not on a virtual machine.

---

### Post by jayon on 2014-08-10
thanks for your reply! you  are right! but i need a another laptop for that! :(
1 more question!
pc1--cloud controller & ll installed in virtualbox
pc2--Node controller
so where will i open the browser to access the cloud ?? PC1 or pC 2??

---

### Post by nerdtron on 2014-08-10
How do you access the cloud? I bet you access it on a web browser using it's IP address of the cloud controller right? Then any web browser on your network will do. Even other PCs. Also, PC2 will be used as a NODE Controller so I guess that pc won't have a GUI and it won't have a browser too right?

---

### Post by jayon on 2014-08-10
exactly! just makin it clear! Thanks a ton! now i know everything about ubuntu cloud! 
Yay! learned on ma own! installed ubuntu & ubuntu server! just ubuntu cloud remains! & here i go :) :D thanksssssss

---

### Post by jayon on 2014-08-14
one more question where am stuck !!
when i install node controller in physical machine it asks me for DHCP configurartion... what IP address should i enter over there???? 
it shows automatic configuration failed!! Please help .. my last step & then am done !!

---

### Post by jayon on 2014-08-14
can any1 help me with this???
dont know what to do!! how to configure node controller connection ? :(

---

### Post by jayon on 2014-08-14
please guys help me with this? is there anyone who knows the DHCP configuration in Node controller installation?? PLEASE

---

### Post by nerdtron on 2014-08-14
> **jayon said:**
> one more question where am stuck !!
when i install node controller in physical machine it asks me for DHCP configurartion... what IP address should i enter over there???? 
it shows automatic configuration failed!! Please help .. my last step & then am done !!

What is this dhcp configuration that you need, for the server itself or for the VMs that will be hosted? On what part of the installation is this?

---

### Post by jayon on 2014-08-14
pc1- the front end installed (storage controller,cluster & ll) inside vmwar
pc2- installin node controller as physical machine! while installing it checks for DHCP configuration and it fails... so my question is how to do manuall configuration??

---

### Post by jayon on 2014-08-14
for manual configuration it needs ip address, netmask, gateway ,hostname ,domain name
i dont know how to do this!!! seariouslyfreaked up!!

---

### Post by jayon on 2014-08-14
[COLOR=#3E3E3E]for manual configuration it needs ip address, netmask, gateway ,hostname ,domain name i dont know how to do this!!! seariouslyfreaked up!![/COLOR]

---

### Post by nerdtron on 2014-08-14
> **jayon said:**
> [COLOR=#3E3E3E]for manual configuration it needs ip address, netmask, gateway ,hostname ,domain name i dont know how to do this!!! **seariouslyfreaked up!!**[/COLOR]

You're installing a cloud environment and setting up a static IP address is freaking you out? Consult your network team and get these details for your computer. Hostname and domain name you can choose them yourself.

---

### Post by jayon on 2014-08-14
okayyyyy my bad!
so what should i enter in PC 2 ??? the details of PC 1???
pc 1-i/p address , netmask & ll???  dont have much information ! sorrry :'(

---

### Post by nerdtron on 2014-08-14
It would be better if your PC1, PC2 and VM for the controller would be on the same network just for easier troubleshooting.

---

### Post by jayon on 2014-08-14
okay then tell should i configure DHCP in windows 7 (PC 1)??
then use those details in PC 2 ?

---

### Post by jayon on 2014-08-14
i guess its difficult to install  front end in virtual machine and node controller in physical machine!!
i  give UP!!
thanks for the reply and support !

---

