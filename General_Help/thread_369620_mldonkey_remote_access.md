---
title: "mldonkey remote access"
date: 2007-02-24
forum: General Help
---

### Post by yb202 on 2007-02-24
Hi everyone. I could really use some help with the ubuntu install of mldonkey (from repository) on a headless server. I isntalled it ok , I've set allowed I.P.s to my whole internal IP range. 

  allowed_ips = [
  "127.0.0.1";
  "192.168.1.0-192.168.1.255";]

Is my syntax wrong? I keep getting an error message "Connection from 192.168.1.66 rejected (see downloads.ini, allowed_ips)" I am behind a router with all ports closed so I think I should be reasonably safe opening the entire range.Please let me know what I am doing wrong as I cant figure it out, all the information I tried points to this setting. I've even set my computer's router assigned I.P. to static and entered that i.p. address into downloads.ini , but didnt help :(. Any help would be greatly appreciated.

---

### Post by yb202 on 2007-02-25
Thats ok , I've solved it :)  . I was editing the wrong downloads.ini file . Apparently there are 2. The one I should have edited was in my home directory , not in /var/lib/mldonkey/......Oh well , another lesson learnt.

---

