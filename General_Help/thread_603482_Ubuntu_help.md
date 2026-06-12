---
title: "Ubuntu help"
date: 2007-11-05
forum: General Help
---

### Post by slyerfox on 2007-11-05
hi im a total newbi on the linux scene downloaded ubuntu 7.1 got it installed no problem but i seem to have 3 main problems 
1- cant get internt connection using a speedtouch 330 black modem- which seems odd because if i turn on my windows pc it shares the net connection fine ?
2- cant get the synaptic package installer to find any software although is this because i dont have the net connected also happens when sharing the connection with my other windows pc?
3- do i need to install the cd drivers that came with motherboard graphics card etc or do i use the synaptic to look for them, if i have to use the cd drivers i have found most are tar.gz files can extract the files ok but have no clue as what to do next to install them ?
hope some1 can help me  thanks.

---

### Post by si4u on 2007-11-05
3 - read the README file for installation

most of the time: 

./configure
make
make install

---

### Post by slyerfox on 2007-11-05
what s the config thing all about then is that code i enter in a terminal windoww /?

---

### Post by slyerfox on 2007-11-05
ok just looked in the read me file and it seems i need sum decompiler prog to start with but how do i load that on ? suggests gcc? went to web site an came bk with loads of files not sure which 1 or all to use sum how

---

### Post by Solarus on 2007-11-05
Hi Slyerfox
With relation to your network problem, if you open a terminal and type the following

sudo ifconfig

does it should your adapter with an associated IP address?

Have you also checked in Network to ensure that you have a dns server specified?

Thanks

---

### Post by slyerfox on 2007-11-05
ok wel as im using the only modem i have on this pc while i try an sort my other linux pc i cant very easily swap the connection as i would have no net   whats an adaptor mean i only have a speedtouch 330 modem is that what ur reffering too ?

---

### Post by slyerfox on 2007-11-05
no there is no dns selected where can i find this information ?

---

### Post by slyerfox on 2007-11-05
ok went bk onto windows pc did the old ipconfig/all and have the dns server address s but where in network do i enter them all i have in network is a windows network icon and then my other pc icon ?

---

### Post by slyerfox on 2007-11-05
souldihve netco in thrweri wol put the dns ???

---

### Post by slyerfox on 2007-11-05
should i have a net icon in there where i would put the dns?

---

