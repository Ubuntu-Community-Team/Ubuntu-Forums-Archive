---
title: "How Can i Make My Lap Top &quot;Server&quot;"
date: 2007-07-31
forum: General Help
---

### Post by Sawa4.CoM on 2007-07-31
[B]hello , 

iam useing linux but what i will need to make it aserver 

my machine is 

top - 11:02:17 up  2:25,  3 users,  load average: 0.27, 0.43, 0.40
Tasks: 108 total,   3 running, 104 sleeping,   0 stopped,   1 zombie
Cpu(s): 12.4%us,  2.3%sy,  0.0%ni, 84.6%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
[COLOR="Blue"]Mem:   1019392k [/COLOR]total,   753948k used,   265444k free,    27768k buffers
Swap:  1951856k total,        0k used,  1951856k free,   422952k cached


pls advice.[/B]

---

### Post by AZzKikR on 2007-07-31
> **Sawa4.CoM said:**
> hello , 

iam useing linux but what i will need to make it aserver 


What exactly do you mean? Specify the word *server* in this context. As in: what do you want the laptop to serve?

Every computer can be seen as a server, as long as it 'exposes', what I call, 'services'. For instance, LDAP directories, Samba shares, Apache, SSH(remote access) and what not. If you want to install Ubuntu as a server instance, I advice you **not** to use a laptop. Too much energy use, gets way to hot most of the time, uses too much energy. And it's just not common to do so. You can download an [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

---

### Post by Sawa4.CoM on 2007-07-31
> **AZzKikR said:**
> What exactly do you mean? Specify the word *server* in this context. As in: what do you want the laptop to serve?

Every computer can be seen as a server, as long as it 'exposes', what I call, 'services'. For instance, LDAP directories, Samba shares, Apache, SSH(remote access) and what not. If you want to install Ubuntu as a server instance, I advice you **not** to use a laptop. Too much energy use, gets way to hot most of the time, uses too much energy. And it's just not common to do so. You can download an [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

thanks for your fast repley 

iam allready useing Ubuntu 7.04 right now 

but i need to use my laptop as " areall server " 

i need to be more good in linux coz iam working at arabian web hosting company who sell hosting an manage servers " LINUX " .

i need to use my laptop as aserver and learn evry thing on it step by step i can be more good on linux so i can be moved at the company from " forums and hosting support team " 

to " Linux Server's Support Team " 

Thanks

---

### Post by Sawa4.CoM on 2007-07-31
NOTE : iam not going to run sites on it  , but iam going to learn how servers going on and how can i fix DB problems , ssh & firwall , Apache " 

also i will  run cPanel ,Control panels 

need it to seems like areall Linux server 

thanks

---

### Post by AZzKikR on 2007-07-31
> **Sawa4.CoM said:**
> NOTE : iam not going to run sites on it  , but iam going to learn how servers going on and how can i fix DB problems , ssh & firwall , Apache " 
also i will  run cPanel ,Control panels 
need it to seems like areall Linux server 
thanks

Okay, first things first. A server, like I said, can be any type of computer. It can be a 400 Mhz Intel machine from 1994, a 1 Ghz from 1999, a laptop, or even a [barebone]("http://www.shuttle.com/"). For instance, I have three computers at home: my server box, my desktop PC and my laptop:

My **server box** is totally dedicated to Apache Tomcat (JSP Webpages), MySQL, LDAP, SSH Remote Access, IRC, you name it. It has no user interface installed (no Gnome/KDE/Xfce). I do administration through the terminal using SecureSHell (SSH).

My **desktop computer** almost has the same application installed like my server box, to do development. You can see my desktop computer as a server computer too, because it serves 'services' to other computer. The difference is, that this computer has Gnome installed, and I can do all kinds of graphical work on it, and play games etc.

My **laptop** can be seen as a sort of duplicate of my desktop computer. It also has service exposed to the other computers.

Basically, there is no real difference between a desktop or server version of Linux. Most of the time it is just the graphical shell which is missing.

What you need to do, is get SSH working. Be prepared to use the terminal _a lot_, and I mean **_a lot**_. I am telling you this, because like I said, most of the time a server box does not have a graphical shell. You will need to type commands to administer your server. 

After you got that working, learn how to install/manage all your needed applications: Apache, IPTables (which is your firewall), MySQL/PostgreSQL or whatever database.

---

### Post by Sawa4.CoM on 2007-07-31
Thank you  . 

thats veryy cool 

so how can i get this service on my normal linux 

1- Apache

2- mysql

thanks

---

### Post by AZzKikR on 2007-07-31
Are you familiar with apt-get / Synaptic / Aptitude on Debian based systems (like Ubuntu)? They are package managers, which let you install certain software by a simple command.

For instance, to install Apache and MySQL you can type something like this in the terminal (not sure whether it is correct, it is just for example purposes):

```
sudo apt-get install *packagename*
```
for example
```
sudo apt-get install httpd
sudo apt-get install mysql
sudo apt-get install sshd # to install the SSH daemon
```

They will download the packages from the repositories, which are in the **/etc/apt/sources.list** file. 

Also, I would recommend a lot of reading on Linux based systems, on how it exactly works. I am not trying to be offensive here, but I want you to know that asking questions in forums only is not *the* way to learn Linux :)

---

### Post by AZzKikR on 2007-07-31
Oh, and check [this website for easy installation commands and short howto's]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"). I've used it frequently in my starting days of Ubuntu. Those commands help you install Apache, MySQL, Samba etc. etc.

---

