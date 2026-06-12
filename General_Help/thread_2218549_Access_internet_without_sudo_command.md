---
title: "Access internet without sudo command"
date: 2014-04-21
forum: General Help
---

### Post by fahim2 on 2014-04-21
I use Internet using a CDMA model using Wvdial . when i dial my modem then i use 'sudo wvdial &' it works fine but i can not access Internet via terminal or in any application without sudo command ..

For example when i do wget URL then it doesn't work but sudo wget URL works .. i use Sublime Text editor and i need Internet access to download plug in . But when i use sudo sublime then it works downloading plug-in but if a edit a file, ***it changes permission and group to root*** rather then username and file does not run in server.

What should i do after dialing my modem as sudo wvdial so that my apps can use Internet without sudo .. normally ..

---

### Post by kc1di on 2014-04-21
you could try using gnome-ppp it's a front end for wvdial and may avoid having to use the sudo command. 
I don't use wvdail any longer but you may be able to change it's permissions also.  I'm assuming since I don't have it install that it's 
exicution file is found in /usr/bin you could change it's permissions by going to the terminal and typing the following command.

```
chmod 777 /usr/bin/wvdial 
``` that would give everyone permission to execute the file. That is assuming it's located in /usr/bin -- you will have to find it. it may be in sbin can't remember. 
good luck

---

### Post by fahim2 on 2014-04-21
i have chmod wvdial and after that when i run wvdial without sudo .. i get

> lenovo@lenovo-Lenovo-G500s ~ $ wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: Permission denied
--> Cannot open /dev/ttyUSB0: Permission denied
--> Cannot open /dev/ttyUSB0: Permission denied

and if i try to install gnome-ppp then ..


> The following packages have unmet dependencies:
 gnome-ppp : Depends: wvdial but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by steeldriver on 2014-04-21
Have you tried adding your regular user to the dialout group?

```
sudo gpasswd --add *username* dialout
```

---

### Post by fahim2 on 2014-04-21
tired ..but didnt work ...

---

### Post by steeldriver on 2014-04-21
.. you will need to log out and back in for the new group to take effect, sorry should have mentioned that

---

### Post by kc1di on 2014-04-21
I should have told you to use sudo so the command should have looked like this ```
sudo chmod 777 /usr/bin/wvdial
```  and like I said I don't have wvdial installed here so not sure that it's in /usr/bin  you may have to look for the correct address. 

Steeldriver's suggestion should have worked also.

---

