---
title: "Apt-get &quot;broken&quot;"
date: 2014-07-16
forum: General Help
---

### Post by OrangeMadness on 2014-07-16
Somehow I managed to mess up apt-get 

louis@laptop:~$ sudo apt-get install openvpn
[sudo] password for louis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
-----> Stucks here, CPU 100%

This happens for all packages. 
The system is Ububtu 12.04LTS Desktop versions. Any ideas?

---

### Post by AnotherKevin on 2014-07-16
I have 2 suggestions:  1.) Upgrade your distro, 2.) Install Synaptic.  

Do you have the built in Software Center?  If so, use that  

Sorry.  I have NO idea how to fix apt-get...

Good luck!  If you find a fix, please post it.  I like apt-get...:p

Kevin

---

### Post by OrangeMadness on 2014-07-16
Followed this:
[http://serverfault.com/questions/368669/debian-ubuntu-is-it-possible-to-reinitialize-var-lib-apt-lists-and-var-apt-cac](http://serverfault.com/questions/368669/debian-ubuntu-is-it-possible-to-reinitialize-var-lib-apt-lists-and-var-apt-cac)

Deleting the lists and updating with apt-get update to re-initialize seems to have done the job.

*
*
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main libxtables10 amd64 1.4.18-1.1ubuntu1 [25.2 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main openvpn amd64 2.3.2-4ubuntu1 [439 kB]
*
*
.Setting up openvpn (2.3.2-4ubuntu1) ...
* Restarting virtual private network daemon(s)...                               *   No VPN is running.
Processing triggers for libc-bin ...
*
*

The only difference is that now I have switched to the US repository instead of my usual local CY one but I can live with that.

---

### Post by deadflowr on 2014-07-16
Moved to ***General Help***

---

