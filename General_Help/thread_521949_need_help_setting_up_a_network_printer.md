---
title: "need help setting up a network printer"
date: 2007-08-09
forum: General Help
---

### Post by devin0 on 2007-08-09
I have a windows xp computer with a cannon pixima ip1700 printer attached via usb. my Ubuntu   machine is on the same network as the windows computer. how do i set up my ubuntu machine so that it can print to the printer on my windows xp machine?

---

### Post by linuxwizard on 2007-08-10
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by devin0 on 2007-08-10
It told me to :

Printing to Windows XP printer from Ubuntu

Prior to setting up the printer in Ubuntu, ensure the printer is installed and shared on the Windows XP machine. 

To add the printer in Ubuntu, 

Go to System -> Administration -> Printing and open the New Printer icon. 

Select Network Printer and Windows Printer (SMB) 

At Host, enter the computer name or IP-address of the Windows XP machine. 

At Printer, enter the share name of the printer. 

At Username, enter guest. 

Test it! 

If it doesn't work, on the XP box: 

Go to Control panel -> Printers & faxes 

Right-click on Printer -> Properties -> Ports tab 

Uncheck "enable bidirectional support" 


i know that my printer is installed and working on my windows machine, i just don't know how to share it. can you please tell me how?

---

### Post by devin0 on 2007-08-11
never mind... after messing around with some settings on my xp box i got it to work. thank you for the instructions linuxwizard :)

---

### Post by jegrcek on 2007-08-16
Very good site, but i dont understand what to do here: 
6. Choose Connect to a printer on the internet and type [http://SERVER_NAME:631/printers/PRINTER_NAME](http://SERVER_NAME:631/printers/PRINTER_NAME) in the text box and then click next.

Where can i found this server name?

---

### Post by Seisen on 2007-08-16
Your server name is your ip address for example I use a router so mine looks like this

```
http://192.168.1.10:631/printers/
```

---

### Post by jegrcek on 2007-08-16
Thank you Seisen. Working.

---

