---
title: "vmware no internet?"
date: 2007-01-13
forum: General Help
---

### Post by haxer on 2007-01-13
Hello i donwloaded an image .vmx for backtrack 1.0 how to get internet working? :-k

---

### Post by useResa on 2007-01-13
What sort of connection have you set up for your internet in your VM?
Are you using "Bridged" or another?

Furthermore do you connect to the internet from your main OS using a wireless or are you "directly" hooked up?

---

### Post by haxer on 2007-01-13
Im direcly hooked up and i have bridged selected ;)

---

### Post by Hossie on 2007-01-13
Does "directly" mean, that you use PPPoE? If yes, you have to use NAT-networking ("share the Host-IP").

---

### Post by haxer on 2007-01-13
hmmm? :-k  explain some more

---

### Post by useResa on 2007-01-14
> **haxer said:**
> hmmm? :-k  explain some more
I must say, my assumption was that you are using VMWare Server to run this .vmx.

If so, you have various options that you can set for your internet connection of your virtual machine, including "bridged", "NAT" and "custom".

The question about being directly connected or not refers to the way you connect to the internet from your main OS. Depending on the method used, you have to use the "bridged" or the "NAT" option in the VM in order to get internet up and running.

Hopes this clarifies it some more.

---

### Post by haxer on 2007-01-14
so i should use nat? :-k

---

### Post by useResa on 2007-01-14
I think it is worth to try using NAT, it also helped "sleepytom" as you can read [here](http://www.ubuntuforums.org/showpost.php?p=1935976&postcount=4).  ;)

---

### Post by haxer on 2007-01-14
Ok didnt work should i try to restart the virtual?:-k

---

### Post by useResa on 2007-01-14
> **haxer said:**
> Ok didnt work should i try to restart the virtual?:-k
You could try a restart or what may work is the following:
In a terminal **in the VM** give the command
```
sudo ifdown eth0
```to bring down the connection followed by
```
sudo ifup eth0
```to bring up the connection (more information about these commands can be found [here]("http://www.die.net/doc/linux/man/man8/usernetctl.8.html").

Maybe the information that you get from *ifup* will also provide additional clues.

---

### Post by braveerudite on 2007-01-14
I use NAT and never had any problems.  (Sharing the connection with "Host OS"

---

### Post by haxer on 2007-01-15
fixed the problem it was dhcp that wasnt enabeld in backtrack 1.0

---

