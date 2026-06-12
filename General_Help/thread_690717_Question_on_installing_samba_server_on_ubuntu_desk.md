---
title: "Question on installing samba server on ubuntu desktop version"
date: 2008-02-07
forum: General Help
---

### Post by cpthk on 2008-02-07
I am trying to built a server for windows clients to login. I trying to install on the desktop version. I install it by command sudo apt-get install samba. But it gives me a message saying couldn't install and has been replaced to samba-common. It just don't let me install server version. Couldn't I install samba server on a ubuntu desktop version?

Thanks.

---

### Post by SpaceTeddy on 2008-02-08
i am sure if i understand you right... but if you want to install samba, you need to have samba-common installed.
also... what is the exact error message you're getting from apt ? and what version of ubuntu are you using.

if i try to run 
> sudo apt-get install samba
on a fresh ubuntu 7.10 desktop it tells me
> $ sudo apt-get install samba
[sudo] password for ipoese:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  samba-common smbclient
Vorgeschlagene Pakete:
  openbsd-inetd inet-superserver smbfs
Empfohlene Pakete:
  smbldap-tools
Die folgenden NEUEN Pakete werden installiert:
  samba
Die folgenden Pakete werden aktualisiert:
  samba-common smbclient
2 aktualisiert, 1 neu installiert, 0 zu entfernen und 185 nicht aktualisiert.
Es müssen 11,6MB Archive geholt werden.
Nach dem Auspacken werden 9445kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]

sorry about the german, hope you can sort of figure out what it says... but in general, it will simply install samba and it's dependencies... 

does that help in any way ?

---

### Post by duckville on 2008-05-19
If you're not sure of the exact package name, why not do one of the following:
"apt-cache search samba"
or
using synaptic search for the package name.

---

