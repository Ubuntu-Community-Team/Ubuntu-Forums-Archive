---
title: "Network recommendations"
date: 2007-10-17
forum: General Help
---

### Post by Rich78 on 2007-10-17
Hi,

I'm wanting to setup a network on an Ubuntu server for Ubuntu clients to connect to.  

The clients will be connecting to shared directories on the server for storing various documents etc.

Could someone please recommend which protocol I should be using?  NFS, Samba (is this Windows shares only?)?

I want something that will be secure with user authentication.

Thanks.

---

### Post by LanDan on 2007-10-17
if you have all unix/linux machines in your setup then NFS will be your choice, if there is 1 windows box in the mix then go for samba, both linux and windows boxes then can see the shares on the server

[http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html)

---

