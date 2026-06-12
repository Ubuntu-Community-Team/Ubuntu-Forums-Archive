---
title: "Ubuntu Server and Desktop"
date: 2005-10-31
forum: General Help
---

### Post by irv on 2005-10-31
I have installed Ubuntu Breezy desktop on one pc and server on another. Everything is working ok, but I want to administrate the server from the destop. I have two options: Apache Toolbox and Webadmin. I have two question. First, seening I have not setup a graphic interface on the server, can I install either Apache Toolbox or Webadmin on the server? and Second, If I can, what is the procedure on how to do it?

If I install Apache toolbox or Webadmin on my destop I am not sure how to interface to my server? I guss you can tell I am new to server part of Linux. I have had other host all my websites and email, and I am retireing and I want to do it all myself now that I will have the time.
Sure hope someone can give me some direction.

---

### Post by Abild on 2005-10-31
To install webmin on the server use the following command:
sudo apt-get install webmin

Afterwards you can access the administration interface from your desktop computer by entering http://<servers ip>:10000 in your browser.

---

### Post by irv on 2005-10-31
I should have known that, it works the same way as in Windows. But as I recall I thought I needed to us https instead of http?

---

### Post by irv on 2005-10-31
After sudo apt-get install webmin at the server, (which went well), I go to the desktop and in my browser I typed: [http://192.168.0.100:10000](http://192.168.0.100:10000) and nothing happens. So I tried [https://192.168.0.100:10000](https://192.168.0.100:10000) and I get an Error - Access denied for 192.168.0.102 which is my desktop. Do I have to set permisions on my destop or on the server? And where do I go and what do I do?

---

### Post by pietro_spina on 2005-10-31
[QUOTE=irv]After sudo apt-get install webmin at the server, (which went well), I go to the desktop and in my browser I typed: [http://192.168.0.100:10000](http://192.168.0.100:10000) and nothing happens. So I tried [https://192.168.0.100:10000](https://192.168.0.100:10000) and I get an Error - Access denied for 192.168.0.102 which is my desktop. Do I have to set permisions on my destop or on the server? And where do I go and what do I do?[/QUOTE]

Your server must also have that (10000) port open... check to make sure your firewall is not blocking it. But I'd suggest just opening it on the NIC that connects to your LAN not the one to the outside (not until you need access from the outsde anyway)...

---

### Post by irv on 2005-10-31
I have my router set to Webmin TCP Port 10000 for the ip 192.168.0.100 which is a static address on my server. When you talk about opening the port on the server what do you mean and how can I do this? I don't have a firewall blocking this, I don't think I do?

---

### Post by pietro_spina on 2005-10-31
[QUOTE=irv]I have my router set to Webmin TCP Port 10000 for the ip 192.168.0.100 which is a static address on my server. When you talk about opening the port on the server what do you mean and how can I do this? I don't have a firewall blocking this, I don't think I do?[/QUOTE]

Can you describe your LAN a little ASCII art, A little gimp work... or even just words... 

for instance, I have an Ubuntu desktop(NIC = eth0) that connects to my server (NIC = eth1) by crossover cable, the server (NIC = eth0) then connects to my DSL modem with regular CAT5 cable...

Can you ping that computer at 192.168.0.100 ?
use
Applications--->System Tools--->Network Tools

---

### Post by irv on 2005-10-31
I do have an Ubuntu destop (NIC=eth0) and I believe my server is also (NIC=eth0).
My network is setup like this: I have a Wireless conection via radio signal from my dish to a tower. From the dish I have a cable to my radio. from my radio I have cat5 to my router, from my router to my desktop and server I have cat 5 cables I have my ports open on my router for FTP, HTTP, Webmin, etc for ip 192.168.0.100 which is my server. It is a static IP. My desktop is Dynamic and at this moment is 192.168.0.102.
And yes, I can ping my server ip 192.168.0.100 from Applications--->System Tools--->Network Tools.
I hope this info helps?

---

### Post by markthecarp on 2005-10-31
[QUOTE=irv]After sudo apt-get install webmin at the server, (which went well), I go to the desktop and in my browser I typed: [http://192.168.0.100:10000](http://192.168.0.100:10000) and nothing happens. So I tried [https://192.168.0.100:10000](https://192.168.0.100:10000) and I get an Error - Access denied for 192.168.0.102 which is my desktop. Do I have to set permisions on my destop or on the server? And where do I go and what do I do?[/QUOTE]

At this point the server is dening access from the client/desktop. Webmin runs it's own webserver so this is not an apache issue. I've not used webmin in a while but take a look at your /etc on the server box for webmin entries. You'll need to allow access from the local network. Webmin's webserver uses syntax is similar to apache's. 

In my experience I found the command line to be more useful than webmin. I am comfortable with shell access alone. For me webmin broke more things by itself than I did by command line. I stess this is my experience with administrating servers. 

-mark

---

### Post by pietro_spina on 2005-10-31
[QUOTE=irv]My network is setup like this: I have a Wireless conection via radio signal from my dish to a tower. From the dish I have a cable to my radio.
I hope this info helps?[/QUOTE]


um just for fun try this from the server
```
# /etc/webmin/start
```


however from the level of your experience, I'd almost suggest installing a server distro like ClarkConnect. [http://www.clarkconnect.org/index.php](http://www.clarkconnect.org/index.php)
The "Home Edition" is quite good for cutting your teeth on a linux server. It's based on Red Hat so a handfull of things are in different places, but still uses apt-get (just like Ubuntu/Debian)

If you do try out ClarkConnect (from what I can understand of your LAN description) you will want to choose either the "stand alone" or "stand alone - without firewall" mode. 

good luck,
p

PS: You won't need Webmin with a CC server they have their own (very clean) web based interface....

---

