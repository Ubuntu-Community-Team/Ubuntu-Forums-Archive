---
title: "Suspend/Hibernate/Resume Script for CIFS service"
date: 2015-03-02
forum: General Help
---

### Post by juano on 2015-03-02
Hi,

I've got a NAS drive connected to the network but it seems that when hibernating/suspending from my laptop I'm losing the connections with the NAS drive. The NAS is mounted with cifs. I've been through some threads but so far I couldn't find the solution. Any suggestion in how to type the scripts for disconnecting the service when suspend and remount the device when coming back alive again?.

Thanks for your help in advance.

---

### Post by Kirboosy on 2015-03-02
I did a little research on the issue and I found this possible solution: [Mounting Samba Share whenever it's available, unmounting when its not]("http://askubuntu.com/questions/194727/mounting-samba-share-whenever-its-available-unmounting-when-its-not")

Hope that helps!
~Caboose

---

