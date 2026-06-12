---
title: "Another SMB mount question.. :("
date: 2012-12-04
forum: General Help
---

### Post by Stardevelop on 2012-12-04
I'm having this ubuntu 12 machine running and want to connect to a smb share outside my network.

When i use my Apple Laptop i can connect to the share without a problem, but when i try it from the ubuntu machine nothing seems to work... :(

------

When i type in the terminal:

:~$ sudo smbmount \\\\80.80.80.80\\sharename /media/localmountpoint -o username=domain\\username,password=password,rw

I get this back:

mount error(115): Operation now in progress
Refer to mount.cifs(8) manual page (e.g. man mount.cifs)

------

When i type in the terminal:

:~$ smbclient \\\\80.80.80.80\\sharename -UDFS\\username password

I get this back:

Connection to 80.80.80.80 failed (Error NT_STATUS_UNSUCCESSFUL)

------

The guy whose share it is tested it succesfully on his ubuntu machine.. What is going wrong!?

---

