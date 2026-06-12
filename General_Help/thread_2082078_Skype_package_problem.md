---
title: "Skype package problem"
date: 2012-11-08
forum: General Help
---

### Post by Exilepilot on 2012-11-08
I've used the software centre to install skype, I get this error once installed:

```
Selecting previously unselected package skype. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 207999 files and directories currently installed.) 
Unpacking skype (from .../skype-ubuntu_4.0.0.8-1_amd64.deb) ... 
dpkg: dependency problems prevent configuration of skype: 
 skype depends on ia32-libs; however: 
  Package ia32-libs is not installed. 
 
dpkg: error processing skype (--install): 
 dependency problems - leaving unconfigured 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ...
```

It seems that skype isn't detecting ia32-libs, or that I used the wrong command in the terminal. ```
 sudo apt-get install ia32-lib 
```
I've also tried: ```
sudo apt-get install Skype
``` and get the same error if I try to install teamviewer. 

I check my synaptic package manager to see if there was any broken packages, I fixed them, I open skype and nothing happens. 

I really hope you can help, because it's been driving me nuts, also I've forgot to mention, I'm a n00b at ubuntu so keep that in mind. :confused:

---

### Post by Exilepilot on 2012-11-08
Bump

---

### Post by papa33170 on 2012-11-08
Well I was never able to install skype from the software-center.
But you can download the package from skype web site and install it.
It worked for me.

---

### Post by atkrad on 2012-11-08
Hello
Please use trying this command:
```
sudo apt-get install -f skype
```

---

### Post by Exilepilot on 2012-11-08
> **papa33170 said:**
> Well I was never able to install skype from the software-center.
But you can download the package from skype web site and install it.
It worked for me.

I have been downloading the package from skype. :confused:

---

### Post by Exilepilot on 2012-11-08
> **atkrad said:**
> Hello
Please use trying this command:
```
sudo apt-get install -f skype
```

 ```
ricky@ubuntu:~$ sudo apt-get install -f skype
[sudo] password for ricky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 skype : Depends: ia32-libs but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

This is what I get?

---

### Post by atkrad on 2012-11-08
Please use trying this command:
```
sudo apt-get install skype:i386
```

---

### Post by Exilepilot on 2012-11-08
> **atkrad said:**
> Please use trying this command:
```
sudo apt-get install skype:i386
```

Executed the command: 
**Output:**
```
ricky@ubuntu:~$ sudo apt-get install -f skype
[sudo] password for ricky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 skype : Depends: ia32-libs but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ricky@ubuntu:~$ sudo apt-get install skype:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
ricky@ubuntu:~$ 

```

Does this mean anything bad? "E: Unable to locate package skype"; 

After that, I tried to reinstall using the package I got from the website; 
error message in software centre:

```
The following packages have unmet dependencies:

skype: Depends: lib32stdc++6 (>= 4.1.1-21) but 4.7.2-2ubuntu1 is installed
       Depends: ia32-libs but it is not installed
       Depends: lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19) but 1:4.7.2-2ubuntu1 is installed
```

---

### Post by atkrad on 2012-11-08
Your system is 32 or 64 bit?

---

### Post by Exilepilot on 2012-11-08
> **atkrad said:**
> Your system is 32 or 64 bit?

64 bit

---

