---
title: "Update manager giving error."
date: 2007-05-06
forum: General Help
---

### Post by burritomaster on 2007-05-06
Doing nothing out of the ordinary, I click the update manager icon, click install updates and it gives me 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Ive already ran

dpkg --configure -a

In terminal but I dont know what to do from there. Any ideas whats wrong or what I need to do? Sorry if its something really obvious, I'm still new to Linux.

---

### Post by useResa on 2007-05-06
Just a few questions to understand the problem.
After you have done **dpkg --configure -a** you still encounter the same problem?
Have you tried -- in the terminal:
```
sudo apt-get update?
```
If so, what was the outcome of that command?
If the outcome makes no sense to you yet, could you please post the result of both commands here?

BTW: There is no need to apologize for asking questions. If you never ask, you will also not learn. We have all been beginners and I -- until today -- still also consider myself quite novice.

---

### Post by burritomaster on 2007-05-06
When **dpkg --configure -a** is entered, it asks me for superuser privileges. About an hour ago, it did not ask for the superuser privileges and gave me a 
**>** as if it wanted me to enter something, but I didn't know what. But when I tried the update command, it gave me a really long output.


[B]
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable Release                        
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release [6738B]   
]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Fetched 16.0kB in 16s (965B/s)                                                 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/B]

Thats just a sample, I picked the ones with variation to give you a better idea of the problem.

---

### Post by useResa on 2007-05-06
> **burritomaster said:**
> When **dpkg --configure -a** is entered, it asks me for superuser privileges. As the "apt" commands the dpkg command MUST be run as root. You can read more about the root user in the Wiki on [this page]("https://help.ubuntu.com/community/RootSudo"). 
Therefore you should give the command
```
sudo dpkg --configure -a
```
It will ask you for the root password.

It should then resolve your problem. If not, please provide the full result in order to be able to determine your problem.

---

### Post by burritomaster on 2007-05-06
Everything worked after I ran

**sudo dpkg --configure -a**

and entered the password. Thanks.

---

