---
title: "Opening Apache to the world"
date: 2007-05-04
forum: General Help
---

### Post by mevets on 2007-05-04
I have managed to get apache2 installed on feisty, it was only an apt-get away after all. I can be seen on my own network, but I havent been able to configure apache in order to been seen on then Internet.

I found the apache config files in /etc/apache2. These config files are much different than apache on Windows. I eventually figured out apache2.conf included ports.conf, httpd.conf. I added 'Listen 80' to ports.conf and went in to my routers settings via the web interface. I opened port 80 for my local ip address. I still cannot be seen though. This is odd considering when I setup my FTP server all I had to do was run proftpd and open port 21 for myself. Apache has not been that easy. My ISP is Cox Communications and I have heared they sometimes put barriers up to impede apache, though its not as if your not allowed to host your own server. People have told me they block port 80 and that I should Listen to port 8080 and have port 8080 trigger 80. I did that in my web config again, but no luck.

Is there generally something you have to do under feisty to get apache2 to be visible over the Internet? It'd make sense that it wouldnt do that out of the box, security concerns an all.

---

### Post by neouser99 on 2007-05-04
you have to setup apache to listen on port 8080 instead of port 80, after making the change a restart is required
```
/etc/init.d/apache2 restart
```

then you need to setup port-forwarding on your router, like you said, of port 8080 to your server/desktop PC. after all this is done, just browse to [http://your.ip.add.ress:8080/](http://your.ip.add.ress:8080/) and all should be good and well.

-neo

---

### Post by sonofusion82 on 2007-05-04
You might also want to consider checking the firewall rules. If I am not mistaken, default Ubuntu blocks all incoming ports.
I use GuardDog but there are many other firewall configuration tools out there.

---

### Post by mevets on 2007-05-05
i got it to work with port 8080 but it there a way to get it to work with port 80?

---

### Post by cwood06 on 2007-05-09
I just installed apache2 and all i had to do was port forward 80 to my laptop running it.

To check that it worked i got on a neighbors network and tryed connecting and it worked.

---

### Post by mevets on 2007-05-10
hmmm let me try again, you using feisty?

---

### Post by cwood06 on 2007-05-10
yea, Im using fiesty i did a apt-get install and that was it then i could access it via the hostname or ipaddress such as 192.168.1.100

---

### Post by mevets on 2007-05-11
i can to. i can get to it on my network, but other people over the internet cannot see me.

---

