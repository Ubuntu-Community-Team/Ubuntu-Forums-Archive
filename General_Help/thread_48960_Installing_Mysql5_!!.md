---
title: "Installing Mysql5 !!"
date: 2005-07-14
forum: General Help
---

### Post by nformosa on 2005-07-14
Hi Guys,

i'm pretty new to both ubuntu and linux so please be patient!

I'mtrying to install the new beta version of mysql ie mysql v5., and since i have n clue on how to use the apt-get as i don't know what command i need to use to view the package list.. i used rpms or so i thought!

I downloaded the rpm's from mysql site and tried the following:

sudo rpm -ivh Mysql....

but the sytem told me to use alien. So i installed each packag using the alien command!

When i came to run the mysql service, the sytem tried to load the servce but then stopped and showed me a red asterix. When i typed in ps -ef no mysql service was running!!

: Starting Mysql ......................... [COLOR=Red]*[/COLOR]

How can i installl mysql5 on my system and how can i list down all the packages available from the apt-get command!! 

thanks very much
Nick

---

### Post by DJ_Max on 2005-07-14
First of all, don't use RPMs. Second, I don't think Ubuntu keeps mysql 5 binaries cause it's not stable. Time to read the manual
[http://ubuntuguide.org](http://ubuntuguide.org)

---

