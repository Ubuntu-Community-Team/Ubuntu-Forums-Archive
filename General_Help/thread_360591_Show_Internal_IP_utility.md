---
title: "Show Internal IP utility"
date: 2007-02-13
forum: General Help
---

### Post by morior on 2007-02-13
I need a way to show a ubuntu pc's internal IP address while the PC is locked down.  Something like ipaddress from castlesoftware would be great.  I'm trying to setup a few pc's for my company with ubuntu and need a way for the users to tell us what pc they are working on without giving them too much power.

---

### Post by taurus on 2007-02-13
You mean something like

```
/sbin/ifconfig
```

---

### Post by morior on 2007-02-13
How do I create a launcher out of that now?

---

### Post by public_void on 2007-02-13
Create a very basic script for example

```
#!/bin/bash

ifconfig $1 | grep "inet addr"
```
this shows the ip address, broadcast address and network mask. Good thing is it hides the other information, although you need to specify the interface as a script argument, e.g. 
```
./ipaddress.sh eth0
```

---

### Post by morior on 2007-02-13
> **public_void said:**
> Create a very basic script for example

```
#!/bin/bash

ifconfig $1 | grep "inet addr"
```
this shows the ip address, broadcast address and network mask. Good thing is it hides the other information, although you need to specify the interface as a script argument, e.g. 
```
./ipaddress.sh eth0
```

If you can please dumb that down for me, I know very little about scripting.

---

### Post by Ramses de Norre on 2007-02-13
Paste the code in a file ipaddress.sh, then run **sudo chmod +x ipaddress.sh**.
Now you can run the script with **./ipaddress.sh eth0**.
If you move the script to /usr/bin you can also run it like a normal command.

---

### Post by morior on 2007-02-13
> **Ramses de Norre said:**
> Paste the code in a file ipaddress.sh, then run **sudo chmod +x ipaddress.sh**.
Now you can run the script with **./ipaddress.sh eth0**.
If you move the script to /usr/bin you can also run it like a normal command.

That does get me the information I need, but is there a way for a script to open a terminal and run the command all from a double click?

---

### Post by dcstar on 2007-02-13
> **morior said:**
> I need a way to show a ubuntu pc's internal IP address while the PC is locked down.  Something like ipaddress from castlesoftware would be great.  I'm trying to setup a few pc's for my company with ubuntu and need a way for the users to tell us what pc they are working on without giving them too much power.

You could also set up something like Gdesklets which (IIRC) can display the IP (and other handy stuff, like disk space available) on the desktop.

---

### Post by morior on 2007-02-14
> **dcstar said:**
> You could also set up something like Gdesklets which (IIRC) can display the IP (and other handy stuff, like disk space available) on the desktop.

Thank you so very much, Gdesklets FTB net gauge was the perfect answer.

---

### Post by wh0rd on 2007-02-14
You can also try Conky, it's light weight way to display your system stats.

---

### Post by dcstar on 2007-02-14
> **morior said:**
> Thank you so very much, Gdesklets FTB net gauge was the perfect answer.

I also have my Gdesklets show my CPU (and motherboard) temperatures, on a warm day I switch off my BOINC background processing to drop my CPU about 10C......     :)

---

### Post by drivel on 2007-02-14
Is there a command like "ipconfig" in Windows to show IP?

---

### Post by dcstar on 2007-02-14
> **drivel said:**
> Is there a command like "ipconfig" in Windows to show IP?

ifconfig

---

