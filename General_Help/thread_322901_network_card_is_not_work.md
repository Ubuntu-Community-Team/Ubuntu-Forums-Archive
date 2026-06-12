---
title: "network card is not work"
date: 2006-12-21
forum: General Help
---

### Post by bandara772001 on 2006-12-21
i'm install ubuntu lamp server as database sever.it work fine on compaq deskpro pc with on bord nic.last day pc not work some thing wrong with hardwear.so i remove the harddisk and fix it to same modle (compaq desktopro) pc with two nic(onbord one & realtec pci card) . pc comes up with out any erros but network is not work.
i chk with lspci

network card are shwon

but
i  run ifconfig, it shows only 
   lo  

i can't find out where the misstake  pls help some one
thanks
bandara772001

---

### Post by hal10000 on 2006-12-21
try to reconfigure your network (nework-admin). 
Open a terminal window and post the output of the following commands:
[COLOR="Red"]lspci
cat /etc/interfaces[/COLOR]

---

### Post by bandara772001 on 2007-01-01
thanks hl1000
 i found mater
one of my nic notwork proper
bye

---

