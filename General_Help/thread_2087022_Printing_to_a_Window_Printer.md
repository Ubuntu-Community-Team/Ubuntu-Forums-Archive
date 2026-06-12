---
title: "Printing to a Window Printer"
date: 2012-11-22
forum: General Help
---

### Post by jat421 on 2012-11-22
Hi, I have a printer installed on windows server 2003 and I am trying to have ubuntu 12.4 print to that printer. When I do the following command I can see all the printers on the server and the printer that I want to print in the list.

```

smbclient -L 10.10.10.9/Printer/ -U Domain/User

```
But when I try to add the printer
```

smb://10.10.10.9/Printer

```
It gives me a error saying 
```

-bash: smb://10.10.10.9/Printer: No such file or directory

```
Any idea what am I dong wrong? Thanks for any help!

---

### Post by wyliecoyoteuk on 2012-11-22
You probably need to supply a username and password to connect.
Have you tried using the GUI or CUPS?

---

