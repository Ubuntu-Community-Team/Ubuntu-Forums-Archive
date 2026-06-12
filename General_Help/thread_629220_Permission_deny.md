---
title: "Permission deny"
date: 2007-12-02
forum: General Help
---

### Post by angelus_kit on 2007-12-02
Dear 

 i have some issue with permission /etc/...., i knoing without root no any user can write on the files in etc folder, but i have application remote VPN  needs to wirite on the files etc/hosts . 
but when i changed the permisison for the etc/hosts the issue is still deny.

my question is : is there files  logs on ubuntu can  show me where  my  user try write /etc/ ??  

sorry for my Bad english

Best regard

---

### Post by PmDematagoda on 2007-12-02
Why don't you use the file manager in root mode, for example if you have Ubuntu, then do this:-

```
sudo nautilus
```

---

### Post by angelus_kit on 2007-12-02
Dear 

i can use nautilus, but is not my issue, i will explain  when i use my VPNremote , i use it trought web browser like firefox after connect to my office, i run secure application manager but this tools need root mode, or permit user can write on the files in etc/hosts.

i tried to change my hsots file rw-rw-rw but i have still issue, note when i run my connectivity by root i didn't any mistake.  

 when secure application manger start  i need to show in logging files if exist  where user is denied writer, i juste 
know , if on the ubuntou haves logs files show the activity user, i sound from all  /var/logs but don't seek any files to show me activity for users on my ubuntu  

sorry for my english 
Best regard

---

