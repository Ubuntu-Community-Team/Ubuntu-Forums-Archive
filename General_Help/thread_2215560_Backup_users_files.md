---
title: "Backup users files"
date: 2014-04-07
forum: General Help
---

### Post by mahmoud_moosa2 on 2014-04-07
Hello everybody,

i am the only user in the work who is using Ubuntu and still new.
i want to prove to my team mates how much it is power and solid. 

i really love Ubuntu Linux.


in fact, there are windows users using buffalow NAS storage to backup their files.

because no gurantee what will happen to NAS device, what i am planing to do is to buy new brand PC with 12 TB HDD.
and then install Ubuntu and create partition dedicated to the users in each company.

next, i want these users to access ubuntu backup server to open their work files normally do their job and remains in the server. that's it.

total companies i am taking backup for are 5.

my question is, what do you kind members advice me to do? 
please i want simple and seamless solution.

thank you very much for all suggestions and solutions.

Mahmoud Moosa

---

### Post by TheFu on 2014-04-07
You aren't saying anything about 
* the backup tools used. THAT is critical, especially if commercial.
* the required protocols necessary. THAT is critical.
* the required redundancy levels
* the criticality of the data. Is $5 lost for every hour it is unavailable or is $5B/hr the costs. Solutions change based on criticality of the data.
* regulatory mandates - there is almost always some legal require for data retention. Often it isn't about keeping, but purging.
* the network connectivity for all the systems involved.

So .... lacking all that data, all you get is a middle-of-the-road best guess - FreeNAS in a RAIDz2 config. Follow the HCL for FreeNAS and be extremely careful to follow their recommended number of drives in any pool.

Oh - and what are the RTO/RPO requirements?

---

### Post by mahmoud_moosa2 on 2014-04-09
> **TheFu said:**
> You aren't saying anything about 
* the backup tools used. THAT is critical, especially if commercial.
* the required protocols necessary. THAT is critical.
* the required redundancy levels
* the criticality of the data. Is $5 lost for every hour it is unavailable or is $5B/hr the costs. Solutions change based on criticality of the data.
* regulatory mandates - there is almost always some legal require for data retention. Often it isn't about keeping, but purging.
* the network connectivity for all the systems involved.

So .... lacking all that data, all you get is a middle-of-the-road best guess - FreeNAS in a RAIDz2 config. Follow the HCL for FreeNAS and be extremely careful to follow their recommended number of drives in any pool.

Oh - and what are the RTO/RPO requirements?

Hello and welcome,

Thank you for reply.

i will answer what i know because i couldn't get some terms.
to get the picture clear for you, all backup devices are connected to the switch in each company LAN.
each backup device has been givin IP Address.

each device has it's own web interface.

all companies network are routable so i can check and monitor the status of each device through web interface from main office.
simply i open the browser and type in the IP Address of the device along with the username and password.


Ok now here my answers to you:

* backuptools:  WD, Buffalo
* protocols: no protocols
* redundancy: no redundancy, in each device i plugged External Hard Disk, and i configured it to take the backup automatically.

by the way: what does RTO/RPO mean?

Respectfully,

Mahmoud Moosa

---

### Post by TheFu on 2014-04-09
Just trying to help.

> **mahmoud_moosa2 said:**
> 
all companies network are routable so i can check and monitor the status of each device through web interface from main office.
simply i open the browser and type in the IP Address of the device along with the username and password.

Ok now here my answers to you:

* backuptools:  WD, Buffalo
* protocols: no protocols
* redundancy: no redundancy, in each device i plugged External Hard Disk, and i configured it to take the backup automatically.

by the way: what does RTO/RPO mean?

There are wikipedia articles on RTO and RPO. Please read. These are terms used in backup and disaster recovery to gather requirements from the client organization - BEFORE trying to design a solution.

If there is a network, then there are protocols involved. Without knowing all the protocols, I can't recommend anything. CIFS, NFS, SFTP ... there is a protocol used.

I sincerely hope that the web interface from a cheap NAS device is NOT available on the public internet. If going through a VPN, then it is fine. Without a VPN, it is very scary.

---

