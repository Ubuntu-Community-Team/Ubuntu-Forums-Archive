---
title: "Cannot get access using Samba"
date: 2007-08-23
forum: General Help
---

### Post by madelman on 2007-08-23
I have installed and configure Samba in my ubuntu 7.04 and no problems were reported. Now I can see all the windows workstations from my ubuntu machine and access them without any problems. The only issue is that from those windows machines I cannot access my ubuntu, I can see it but when I type the user and password it just does not give access and even from my ubuntu machine when I click on places/network I can see my machine but if I try to list directories it comes back with the same situation saying that I am not authorized. 


I have a folder to share in ubuntu and when I click on it that's when it comes up with the authentication then I enter my user and passwd and no access.

Do you have idea where I should be looking to fix this issue?

thank you.

---

### Post by aJayRoo on 2007-08-23
Did you add a samba user to your system? I don't fully understand the reasons behind this as I don't use samba really but I believe it is necessary to create a samba user to access shares on linux machines. To do this you can use the advice given in [this](http://ubuntuforums.org/showthread.php?t=202605&highlight=install+samba) thread, starting at section 1.1. Hope that helps!

---

### Post by imbjr on 2007-08-23
I had to deal with this recently. There's a command to add a samba user and password you need to do:

sudo smbpasswd -a imbjr

sorted me out.

---

### Post by madelman on 2007-08-24
yeah. Thank you for your answers. That thread aJayRoo  mentioned has 2 commands to create and enable the user in samba and that made the trick. It is working and now I can access ubuntu from windows. 

cheers.

---

