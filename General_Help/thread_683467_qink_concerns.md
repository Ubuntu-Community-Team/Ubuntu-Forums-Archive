---
title: "qink concerns"
date: 2008-01-31
forum: General Help
---

### Post by Joe_Linux on 2008-01-31
I am trying to use qink, it is not able to see my usb printer, The program is asking for my printers usb port number. I ran lsusb 
joe51@joe51-desktop:~$ sudo lsusb
[sudo] password for joe51:
Bus 005 Device 002: ID 0ace:1215 ZyDAS 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000  
joe51@joe51-desktop:~$ 

Is my printers usb port number here ?

---

### Post by Joe_Linux on 2008-02-02
joe51@joe51-desktop:~$ sudo chmod 666 /dev/usblp0005
[sudo] password for joe51:
chmod: cannot access `/dev/usblp0005': No such file or directory
joe51@joe51-desktop:~$ sudo chmod 666 /dev/usblp04b8:0005
chmod: cannot access `/dev/usblp04b8:0005': No such file or directory
joe51@joe51-desktop:~$ sudo chmod 666 /dev/usblp04b8
chmod: cannot access `/dev/usblp04b8': No such file or directory
joe51@joe51-desktop:~$  sudo chmod 666 /dev/usblp002
chmod: cannot access `/dev/usblp002': No such file or directory
joe51@joe51-desktop:~$ 

Showing that I am trying things, that so far do not work, help would be appreciated. 

 Joe

---

