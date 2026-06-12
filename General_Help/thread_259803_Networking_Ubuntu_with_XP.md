---
title: "Networking Ubuntu with XP"
date: 2006-09-17
forum: General Help
---

### Post by andyrobo60 on 2006-09-17
I am running ubuntu on my pc and xp on my laptop. They both use the same router and the internet works fine on both. But I have been having some problems with the network. 

Ubuntu has both samba and ssh installed on it. I have followed guides to set both up. But I am still not able to see my shared files on my laptop from my pc or visa versa. When I try to connect to my pc from my laptop using ssh (PuTTY) I get the message "Network error: Connection timed out". 

I think that they cant communicate with each other. While both can communicate with the router. Does anyone know what might be causing this problem.

---

### Post by marianom on 2006-09-17
Can you ping each machine from the other?

It seems thewy don't see each other:
[http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-conntimedout](http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-conntimedout)

---

### Post by Leeghoofd on 2006-09-18
Have you checked for possible problems in firewallconfigurations?

I've had the same problem with sygate running on my XP machine.
Its logical to have your systems trust eachother by default , but just double check anyway.

In addition as already mentioned its a good idea to run a ping command on both XP and linux and check wether communication is working on low level.

---

### Post by andyrobo60 on 2006-09-18
Yes both can ping each other. I have tryed setting my xp firewall (sygate) to "allow all" but that dosn't change anything.

---

### Post by pod25 on 2006-09-18
Can you post the contents of your network here.

Networking from ubuntu to windows is very easy and you really should not have to do much to gain that, so I suggest turning your windows firewall off, then try again.

---

### Post by andyrobo60 on 2006-09-18
FIXED! but now I feel very stupid. When I first installed ubuntu I used ubuntuguide.org to find apps that I wanted to install. One of the apps I installed was firestarter (a firewall). I had forgoten about it. And that was stopping both SSH and samba. Sorry for wasting your time.

---

