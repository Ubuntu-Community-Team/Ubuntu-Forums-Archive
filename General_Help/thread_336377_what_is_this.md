---
title: "what is this?"
date: 2007-01-11
forum: General Help
---

### Post by haxer on 2007-01-11
Hello every time i try to install something ive get this 

haxer@slackware:~$ sudo aptitude install  streamtuner
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Läser utökad statusinformation
Initierar paketstatus... Färdig
Bygger taggdatabas... Färdig
Inga paket kommer att installeras, uppgraderas eller tas bort.
0 paket uppgraderade, 0 nya installerades. 0 att tas bort och 0 inte uppgraderade.
Behöver hämta 0B arkiv. Efter uppackning kommer 0B att användas.
Skriver utökad statusinformation... Färdig
Ställer in vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.148.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]







how to get rid of it? Ive tried to uninstall vmware trough automatix but it doesnt work ive even tried dkpg --configure -a and it just makes the same. :(

---

### Post by haxer on 2007-01-11
anyone please?:-k

---

### Post by bodhi.zazen on 2007-01-11
Try this:```
sudo mv /etc/vmware/vmnet8/dhcpd/dhcpd.conf /etc/vmware/vmnet8/dhcpd/dhcpd.conf.backup
```

And re-try ...

---

### Post by haxer on 2007-01-11
The file or the catalog isnt there it says what should i do now? :confused: :(

---

### Post by yabbadabbadont on 2007-01-11
If you have uninstalled vmware, manually remove the /etc/vmware directory.  (It gets left behind for some reason)  It should help, but I'm not sure if it will solve all your issues.

---

### Post by haxer on 2007-01-11
Tried to remove the etc/vmware file done that worked good to remove it but my problem isnt solved :( so i tried sudo aptitude remove vmware returned with error so what should i do now? ;) :-k

Is it better to reinstall ubuntu totally? My computer is new got it today havent got to much installed maybe better to reinstall ubuntu?

---

