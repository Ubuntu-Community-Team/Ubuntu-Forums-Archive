---
title: "Wrong UPS status"
date: 2020-06-26
forum: General Help
---

### Post by gripfly on 2020-06-26
Hi there


I  am running Kubuntu with an EATON UPS. 
However, Kubuntu shows me that  the UPS is at 0%, plugged in and not  charging. 
Unplugging the USB  connection removes the battery widget in the taskbar. 
Once plugged in, I do see two more tabs in the Energy saving settings named "On Battery" and "On Low Battery".

Do I  need to enable something  specific to make that work?


Thanks in advance.

[ATTACH=CONFIG]286323[/ATTACH][ATTACH=CONFIG]286324[/ATTACH]

---

### Post by lvm on 2020-06-27
This is for notebooks. For UPS you have to install UPS management software e.g. nut if your UPS is supported [https://networkupstools.org/ddl/Eaton/](https://networkupstools.org/ddl/Eaton/) Or check if Eaton has proprietary linux software.

---

### Post by gripfly on 2020-06-28
Thanks for that. Meanwhile I found out that there is a Software to manage all that Eaton provides (well, actually 2). 

   	There is ***Eaton Intelligent Power Protector (IPP)*** and ***Eaton Intelligent Power Manager* (IPM)**. 

   	   	Thanks for that. 

   	The difference between these two can be read here: [https://community.spiceworks.com/topic/1138829-difference-between-intelligent-power-manager-ipm-and-protector-ipp](https://community.spiceworks.com/topic/1138829-difference-between-intelligent-power-manager-ipm-and-protector-ipp) 
   	There is a **User's Guide for IPP**, which is very helpful: [https://www.eaton.com/content/dam/eaton/products/backup-power-ups-surge-it-power-distribution/power-management-software-connectivity/eaton-intelligent-power-protector/eaton-ipp-user-guide-p-164000291.pdf](https://www.eaton.com/content/dam/eaton/products/backup-power-ups-surge-it-power-distribution/power-management-software-connectivity/eaton-intelligent-power-protector/eaton-ipp-user-guide-p-164000291.pdf) 

   	  
   	After installing the Software you need to open the Web interface: [https://localhost:4680/](https://localhost:4680/) 
   	Then login with; User: admin, PW, admin 
   	  
   	This is all what's needed. Then you can manage all the stuff. However, I  still have the issue that once the UPS shuts down the System, there is a  connection failure afterwards. After about 2h the communication failure  somehow resolves itself and it works again. 
   	  
   	I made a post regarding this issue here (haven't gotten any response  yet tho but if there will be ever an answer to this, it might be there):  [https://community.spiceworks.com/topic/2278555-eaton-5sc-communication-failure](https://community.spiceworks.com/topic/2278555-eaton-5sc-communication-failure)

---

