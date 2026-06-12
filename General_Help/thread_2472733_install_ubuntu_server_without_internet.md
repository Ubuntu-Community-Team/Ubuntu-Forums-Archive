---
title: "install ubuntu server without internet"
date: 2022-03-10
forum: General Help
---

### Post by robertkwild on 2022-03-10
hi all,


is there anyway to install ubuntu server 20.04.3 LTS  live server without an internet connection ie on a network without  internet access

im installing on a vm and going through the install steps and then it fails on the last stage as it requires intenret

is there anyway to make this work without internet

thanks,
rob

---

### Post by #&amp;thj^% on 2022-03-10
I've used a bogus IPv4 address, then it proceeded with the install.
EDIT: I've checked my notes and that worked on 18.04.4, let me know if that still works here on 20.04.

---

### Post by robertkwild on 2022-03-11
issue solved, just disabled the NIC on the vm and then it installed no problem


once it installed i enabled the NIC and in netplan i gave it a static ip


this was the problem where it was getting the error

[https://i.postimg.cc/52x47yXZ/ubuntu-no-mir.png](https://i.postimg.cc/52x47yXZ/ubuntu-no-mir.png)

it got stuck or gave me error after curtin


tbh i dont like this new ubuntu aproach ie cloud-init, not impressed

---

### Post by TheFu on 2022-03-11
Please mark this thread **_SOLVED_** (*thread tools button*) so people seeking answers can find it easier and people wanting to help don't waste their time.

---

