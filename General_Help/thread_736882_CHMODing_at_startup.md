---
title: "CHMODing at startup"
date: 2008-03-27
forum: General Help
---

### Post by ezramorris on 2008-03-27
Hi,
Everytime I use QEMU, I have to run 
```
sudo chmod 666 /dev/kqemu
```,
and whenever I use VirtualBox, I have to run
```
sudo chmod 666 /dev/vboxdrv
```.

So, the question is, can I make this automatically happen at startup (I'd guess yes), and if so, how?

Thanks.

---

### Post by kpkeerthi on 2008-03-27
Put those commands in /etc/rc.local without the **sudo** prefix. But I don't have to do it, really. Are you a member of **vboxusers** group.
```
gpasswd -a <user-id> vboxusers
```
Logout and log back in and verify your group by typing **groups** in command line.

---

### Post by ezramorris on 2008-03-28
> **kpkeerthi said:**
> Put those commands in /etc/rc.local without the **sudo** prefix. But I don't have to do it, really. Are you a member of **vboxusers** group.
```
gpasswd -a <user-id> vboxusers
```
Logout and log back in and verify your group by typing **groups** in command line.

Thanks. I used the group idea, and it worked great. I added the kqemu one to rc.local, but I havent's tested it yet.

Just to clarify, does gpasswd -a do the same thing as adduser?

---

