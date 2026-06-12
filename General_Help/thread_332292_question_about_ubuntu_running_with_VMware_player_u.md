---
title: "question about ubuntu running with VMware player under windows"
date: 2007-01-05
forum: General Help
---

### Post by erv2 on 2007-01-05
Hi,

i am newbie for both linux and VMware, i just installed VMware player in my XP machine and got the "Ubuntu 6.10 (Edgy Eft) server - VMware appliance" from: [http://www.jcinacio.com/projects/VMware-UbuntuServer-6.10/](http://www.jcinacio.com/projects/VMware-UbuntuServer-6.10/)

i hope to build a LAMP server out of and install a ruby on rails server. here are my questions:

1. after i use ./setup.sh to setup those basic setups, it doesn't seem to work, i try to ping the ip address i set for the ubuntu from windows terminal, it cant reach.   what is the correct ip address for the virtual machine if it's not the one i set?

2. i set the hostname to something else, but when i ping it WITHIN the virtual machine, it doesn't understand the hostname, (the default name can point back to localhost).

3. is there any easy way for me to install AMP in one go? something like: sudo apt-get install LAMP

4. this is similar to question 1, how to i test if apache is running outside the virtual machine (i.e. the browser from XP, other machines in my network etc)?

5. can i install a basic x windows and a browser in it?

6. if i want to make it accessible from outside my network, how do i do it?

if some of the questions have been asked before, please excuse my lack of knowledge. i really want to learn ubuntu and dont want to mess up with my machine.

thank you.

---

### Post by erv2 on 2007-01-06
anyone any idea? thanks

---

### Post by koenn on 2007-01-06
1. and 3. depend on how the VMplayer handles networking. You should be able to connect to a VM from the host system if the VM network card is bridged to the real networkcard. I think NAT is also something that might work. 
So you'd need to find out and configure the VMplayer's network config
here's a start:
[http://blog.baeke.info/blog/Technologies/VirtualMachines/_archives/2005/11/28/1425092.html](http://blog.baeke.info/blog/Technologies/VirtualMachines/_archives/2005/11/28/1425092.html)

same thing for 6., and probably 2. as well

5. -yes
3. -there are howto's about this but i don't remember where. maybe google for ubuntu LAMP howto ?

---

