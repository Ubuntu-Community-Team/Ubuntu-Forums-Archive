---
title: "rdp  after cisco vpn"
date: 2012-11-19
forum: General Help
---

### Post by fachhoch on 2012-11-19
I am new bee to ubuntu , I want to connect to my work machine which  is windows  for whihc I installed cisco vpn   , tried connection it  is sucessful. Now the next step is to connect to my machine through rdp .
In windows after I start my vpn client I open rdp enter the ipaddress of my machine and get connected. 
I did the same here but  I get connection to server failed.
also when I try ping my work machine ipaddress   not response.
Please advice, do I need anything more than ipaddress, username/password?

---

### Post by Kirk Schnable on 2012-11-20
It sounds like the VPN communication is not working, because you can't ping your work machine. In this case, the output from these commands might be of use to us, as well as the IP address on the VPN you're attempting to ping. 

```
sudo ifconfig
```

```
sudo route -n
```

Thanks,
Kirk

---

