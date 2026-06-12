---
title: "How to open a custom port?"
date: 2007-10-05
forum: General Help
---

### Post by anhstar on 2007-10-05
I would like to know how to open a custom port like RMI (1099) for example. 
I read that the port in Ubuntu will be opened if the program need it, but I still can't access my server from another comp on the same network using that port (1099).
I don't have a firewall setup on the machine with Ubuntu either. 
The Ubuntu I installed on that machine is Feisty.

Can anyone help me out?

Thank you!

---

### Post by por100pre1 on 2007-10-05
Welcome to the forums! You can use these commands; copy, paste and ENTER each one of these commands, one by one, in Terminal (**Applications> Accesories> Terminal**):

```
sudo iptables -A INPUT -p tcp --dport 1099 -j ACCEPT
```

```
sudo iptables -A INPUT -p udp --dport 1099 -j ACCEPT
```


If you don't want to use commands, you can use Firestarter to open the port. Here's how to install Firestarter:

```
sudo aptitude install firestarter
```

[Here's]("http://www.fs-security.com/docs/interface.php") how to use it.

---

