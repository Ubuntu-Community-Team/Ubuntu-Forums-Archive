---
title: "Nessus stopped working"
date: 2005-09-06
forum: General Help
---

### Post by brea on 2005-09-06
So I was using nessus today and used the package manager to install vnc. After that my next scan reported nothing back giving the error. 'nessus returned a blank report'

nmap works fine so I know I have connectivity to the hosts in question. I tried removing nessus from the package manager and tried reinstalling it twice. Once from the package manager and another from the apt-get option.

Any ideas here would be greatly appreciated.

---

### Post by nic0 on 2005-12-08
I have this problem too.. :/

---

### Post by sysmin on 2005-12-13
brea,

Are you sure that none of your configurations changed when you installed Nessus again? Maybe you are telling the Nessus server to do some sort of verification (TCP or ICMP) to make sure the machines were up first before scanning and that traffic is filtered.

---

