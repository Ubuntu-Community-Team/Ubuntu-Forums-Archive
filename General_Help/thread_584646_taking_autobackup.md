---
title: "taking autobackup"
date: 2007-10-21
forum: General Help
---

### Post by gnw23 on 2007-10-21
Dear All

I am using edubuntu server

i want to use a seperate hdd for edubuntu server and another one just for data

so is it possible to connect 3 hdd 

1) first for software edununtu server
2) second for data of all clients 
3) third to take a backup an autoback of the second hdd  at the end of the day

Any help is appriciated in this regard

Thanx in advance

Shashikant

---

### Post by dcstar on 2007-10-21
> **gnw23 said:**
> Dear All

I am using edubuntu server

i want to use a seperate hdd for edubuntu server and another one just for data

so is it possible to connect 3 hdd 

1) first for software edununtu server
2) second for data of all clients 
3) third to take a backup an autoback of the second hdd  at the end of the day

Any help is appriciated in this regard

Thanx in advance

Shashikant

Set up the second hard disk as the /home mount point (detailed instructions can be searched for), and then just have a script/backup program run by cron to back it up to a formatted filesystem on the other disk - there are many (many) options to do this.

---

