---
title: "Unmet dependencies for Mariadb"
date: 2017-09-29
forum: General Help
---

### Post by cliffmitchell on 2017-09-29
I have started getting errors when running updates as follows:

```
root@ubuntu:~# sudo apt-get update
Hit:1 http://ppa.launchpad.net/pbek/qownnotes/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                       
Hit:3 http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu xenial InRelease                                                        
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                       
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                        
Hit:6 http://www.ftp.saix.net/DB/mariadb/repo/10.1/ubuntu xenial InRelease         
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]      
Fetched 306 kB in 0s (425 kB/s)                              
Reading package lists... Done
root@ubuntu:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mariadb-client : Depends: mariadb-client-10.1 (= 10.1.28+maria-1~xenial) but it is not installed
 mariadb-server : Depends: mariadb-server-10.2 (>= 10.2.9+maria~xenial) but it is not installed
 mariadb-server-10.1 : Depends: mariadb-client-10.1 (>= 10.1.26+maria-1~xenial) but it is not installed
                       Depends: mariadb-server-core-10.1 (>= 10.1.26+maria-1~xenial) but it is not installed
E: Unmet dependencies. Try using -f.


```

I have tried apt-get -f install but still have the problem. My system is running Ubuntu 16.04.3 LTS and ISPConfig 3.1.6.
Any help would really be appreciated.
Many thanks,
Cliff

---

### Post by ian-weisser on 2017-09-29
Why are you running sudo while using the root account?

Your problem looks like a classic *version conflict*. You have three different repositories (Ubuntu, coreix, saix). Different repos provide different packages, and differerent versions of different packages.
The problem is that those different versions conflict - you can have only one version installed at a time. 
Pick one repo, uninstall packages from the others.

---

### Post by cliffmitchell on 2017-09-29
Thanks ian-weisser. I'll try and sort out the repos as you suggest and get back with the results. Thanks for the prompt response.

---

### Post by cliffmitchell on 2017-09-29
Yes, you were absolutely correct. In my sources.list I had somehow managed to get 2 different repositories for mariadb:

deb [arch=amd64,ppc64el,i386] [http://www.ftp.saix.net/DB/mariadb/repo/10.1/ubuntu](http://www.ftp.saix.net/DB/mariadb/repo/10.1/ubuntu) xenial main
and
deb [arch=amd64,i386,ppc64el] [http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu](http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu) xenial main
Deleting the second of these fixed my problem. Thanks you again [**[COLOR=#DD4814][B]ian-weisser**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1841707") for your help, it really is appreciated.
Cliff

---

