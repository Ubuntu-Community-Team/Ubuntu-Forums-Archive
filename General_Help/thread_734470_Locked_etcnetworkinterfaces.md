---
title: "Locked /etc/network/interfaces"
date: 2008-03-24
forum: General Help
---

### Post by metradynamix on 2008-03-24
Good Day All,

I had to give access to my server to  a Tech today, to have my network settings re-entered. System is remote, and in a datacenter. I really didn't want to do so but I had no choice :(

Either way he did something, and now I cannot edit /etc/network/interfaces
I am completely lost, and I have no clue on what is going here.

I cannot chmod, chown or nano save, or even delete the file. 
All of these give me a Operation not permitted message.

Those all executed as sudo or su -s as root@

When I ls -la the permissions seem normal?
-rw-r--r-- 1 root root 133 2008-03-24 17:23 /etc/network/interfaces

Any assistance on this will be greatly appreciated.

---

### Post by kidders on 2008-03-26
Hi there,

Assuming your root filesystem is Ext2/3, what's the output of **lsattr /etc/network/interfaces** ?

---

