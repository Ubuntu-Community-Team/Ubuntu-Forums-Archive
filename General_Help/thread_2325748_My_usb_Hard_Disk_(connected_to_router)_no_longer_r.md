---
title: "My usb Hard Disk (connected to router) no longer recognised"
date: 2016-05-25
forum: General Help
---

### Post by johnaaronrose on 2016-05-25
I used to be able to access my usb hard disk (connected to router) in Nautilus but no longer can do so. This is strange as the router's admin sees it (screenshot attached).

PS on a thread in AskUbuntu, it suggested using the command "sudo mount -o nosuid,uid=<insert uid here>,gid=<insert gid here> //192.168.1.1/USB_Storage/ /media/public/". I tried that but got:
john@Desktop:~$ sudo mount -o nosuid,uid=1000,gid=1000 //192.168.1.1/ExternalHDD/ /media/Public/ 
Password for root@//192.168.1.1/ExternalHDD/:  
Unable to find suitable address.  

Any ideas why?

I get this message irrespective of the password that I type.

---

