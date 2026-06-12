---
title: "ubuntu adduser , newbie questions"
date: 2015-04-13
forum: General Help
---

### Post by ron38 on 2015-04-13
Hi i'm ron , i am beginner with ubuntu and command line , i have this problem in my vps i created new user with command
```
sudo adduser  nameofuser
```
i give to him sudo commands , after when i log in VPS with him and try to install something , all files are saved in the root not /home/nameofuser/..... how can i make save in home directory of user ?  and how can i limit the powers of root ? or better how can i delete ? and use only the new user ? is this possible ? 
```
# User privilege specification root 
ALL=(ALL:ALL) ALL newuser 
ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

 # Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives: 
#includedir /etc/sudoers.d

```i can not understand what %admin and %sudo groups do ? can i delete this ? or its important ? sorry i'm beginner

---

### Post by ian-weisser on 2015-04-13
Please explain the exact steps he is using to 'install something' while logged in.

---

### Post by grahammechanical on 2015-04-13
It is standard practice in Linux/Ubuntu for application files to go in several different directories under root ( / ) and user application configuration files to go in the /home/username folder. You may be seeing what is the standard way of working in Linux.

Regards.

---

### Post by ron38 on 2015-04-14
Hello this is what i do :  ```
  logged by SSH with root   sudo adduser faenk  visudo   faenk ALL=(ALL:ALL) ALL  close root  logged by SSH with  faenk  sudo apt-get install lamp-server^  
```   its all ok but the problem are : the lamp-server are not saved in /home/faenk/ etc...  but its saved in root i think because example if i try to open by root this file   sudo nano /etc/mysql/my.cnf    i can open it but i never installed lamp-server^ in root ,  i installed on faenk    so my questions are : how can i make all installed things be save in home/faenk/lamp-server^  etc ?  and maybe how can i after disable root ?

---

### Post by ian-weisser on 2015-04-14
> **ron38 said:**
> the problem are : the lamp-server are not saved in /home/faenk/ etc...  but its saved in root i think because example if i try to open by root this file   sudo nano /etc/mysql/my.cnf    i can open it but i never installed lamp-server^ in root ,  i installed on faenk    so my questions are : how can i make all installed things be save in home/faenk/lamp-server^  etc ?  and maybe how can i after disable root ?

That doesn't seem like a problem to me.
Applications are not saved in /home/faenk, nor in /root. They never have been. That's not the purpose of those directories.
Example: /etc/mysql/my.cnf is not in /root, it's in /etc. It's *owned* by root so nobody else can change the systemwide settings.


Debian packages can be installed to only one location...and you don't get to choose the location. The package tells the package manager where to install.
You can see an example using the command 'dpkg -L mysql-client-core-5.5' (or any other package you have installed)

Are you having trouble starting and configuring your new LAMP server?
Have you consulted the [LAMP page of the Ubuntu Wiki]("https://help.ubuntu.com/community/ApacheMySQLPHP")?

FYI, enabling root on your Ubuntu system is discouraged. Your system includes sudo specifically so you don't need to enable root.
Enabling root login on your ssh server is also discouraged.

---

### Post by ron38 on 2015-04-14
i' understand now ,  the adduser its for ?  i mean /home/username/

---

### Post by ian-weisser on 2015-04-14
The 'adduser' command creates a new user account, login, and /home/ directory.
It can also create system (non-human) users, like a limited-purpose user to run a LAMP server, so an exploit in the server won't compromise the rest of the system.

The /home/faenc/ directory is for storing faenc's *personal* data, mail, web browser cache, personal settings, files, recreations, desktop, scripts, fonts, and much more.
Personal applications can go there, too.

Systemwide applications are usually installed to /bin, /sbin, or /usr. Systemwide data is stored in /var or /usr. Systemwide settings are stored in /etc

---

