---
title: "enabling xdmcp"
date: 2005-10-21
forum: General Help
---

### Post by yerffej on 2005-10-21
Has anyone successfully enabled xdmcp in kdm on Kubuntu. I have enabled it successfully on other distros by editing kdmrc and xaccess but that procedure doesn't seem to work in Kubuntu. Am I missing something?
I am running the 64 bit version but I wouldn't think that should make a difference.

---

### Post by arnieboy on 2005-11-09
[QUOTE=yerffej]Has anyone successfully enabled xdmcp in kdm on Kubuntu. I have enabled it successfully on other distros by editing kdmrc and xaccess but that procedure doesn't seem to work in Kubuntu. Am I missing something?
I am running the 64 bit version but I wouldn't think that should make a difference.[/QUOTE]
have u tried the following thread?
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP-KDM](http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP-KDM)

---

### Post by sfy on 2006-02-28
Hi, 

I have this problem too. I have followed at least 3 different tutorials on xdmcp. In:

/etc/kde3/kdmrc
[Xdmcp]
Enable=true
Willing=/etc/kde3/kdm/Xwilling
...
/etc/kde3/Xaccess
*
...
netstat -l  shows that xdmcp is listening:
udp6       0      0 *:xdmcp                 *:*

I have not setup any ACLs or firewall systems. I am also able to connect to other listening ports. 

Any idea what to do?

---

### Post by jv2006 on 2006-03-03
This seems to be a problem with ipv6. Kdm is listening on udp6 and not on udp. I found remarks where people said that the problem is solved with kde 3.5. The other solutions (for example adding a line
> LISTEN 0.0.0.0
in the file
> /etc/kde3/kdm/Xaccess
did not work.

---

### Post by KermitJr on 2006-03-07
I finally got it to work.

I opened synaptic and did "Complete removal" of:

kdm
kdebase-bin

Then:
```
apt-get install kubuntu-desktop
```
This uninstalled and re-installed a large amount of programs and one prompted to overwrite the kdmrc file with an updated one.  I said yes and continued.

At the end end, I edited ```
/etc/kde3/kdm/kdmrc
``` to ```
[Xdmcp] enable=true
``` and restarted kdm via: ```
sudo /etc/init.d/kdm restart
```
Voila! now  ```
Xnest -query localhost :1
``` gives me a kdm login screen.

I'm not sure why simply trying to update didn't rewrite that kdmrc file, but the newer version is significantly different from the older version.

(PS: Don't forget to change the /etc/kde3/kdm/Xaccess file line #*     to *   )

---

