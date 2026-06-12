---
title: "Ubuntu 14.04.5 broken held packages"
date: 2016-10-17
forum: General Help
---

### Post by thinkfast2 on 2016-10-17
Dear All,

I need your assistance with the following issue, when i am trying to install cacti on my Ubuntu server i am receiving the following error:
> The following packages have unmet dependencies: mysql-client : Depends: mysql-client-5.5 but it is not going to be installed
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
 php5-mysql : Depends: phpapi-20090626
              Depends: php5-common (= 5.3.10-1ubuntu3.25) but 5.5.9+dfsg-1ubuntu4.19 is to be installed
 php5-snmp : Depends: libsnmp15 (>= 5.4.3~dfsg) but it is not going to be installed
             Depends: phpapi-20090626
             Depends: php5-common (= 5.3.10-1ubuntu3.25) but 5.5.9+dfsg-1ubuntu4.19 is to be installed
 snmpd : Depends: libsnmp15 (>= 5.4.3~dfsg) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.




Could you please advise?

Thank you in advance.

---

### Post by oldrocker99 on 2016-10-17
Welcome to the forums!

Try this:```
sudo apt-get -f install
```

This **might** fix the problem, but if the files don't exist on the server, you're kind of out of luck.

I did successfully install cacti just now from within Synaptic, BTW.

If you don't have Synaptic installed, do this:```
sudo apt-get install synaptic
```

Good luck!

---

### Post by ian-weisser on 2016-10-17
> **thinkfast2 said:**
> *Depends: php5-common (= 5.3.10-1ubuntu3.25) but 5.5.9+dfsg-1ubuntu4.19 is to be installed*
5.3.1.10 is from Ubuntu 12.04.
5.5.9 is from Ubuntu 14.04...though it has since been superseded.
You have introduced a version conflict onto your system.

Which version of Ubuntu are you using?
Eliminate the non-Ubuntu or wrong-version sources, and uninstall all software from those sources, to resolve the problem.

---

