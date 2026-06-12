---
title: "opened ports"
date: 2005-10-15
forum: General Help
---

### Post by djdanx on 2005-10-15
Hey there !

I just installed ubuntu 5.10 and im really impressed...
anyway i installed bittornado and i know that my 113 is only open port
but bittornado says failed : 113. 
So ubuntu has some firewall installed or something ?
how to re-open ports ?

---

### Post by ince on 2006-06-08
I have the same problem. My only open port is 113 and I can't get azureus working. Ubuntu is blocking every port < 1024.  I don't want yo run programs as root because it's unsafe.

---

### Post by ifokkema on 2006-06-08
[QUOTE=ince]I have the same problem. My only open port is 113 and I can't get azureus working. Ubuntu is blocking every port < 1024.  I don't want yo run programs as root because it's unsafe.[/QUOTE]

Ubuntu does not come with a firewall activated by default. But ports are not open if nothing is listening. You need a daemon listening at a port, for it to 'open'. For instance, port 80 is 'closed' unless you install a webserver.

I have no knowledge of any of the programs mentioned here, but you can check your open ports by running:
```
nmap IP_ADDRESS
```

You may need to install nmap first:
```
sudo apt-get install nmap
```

---

