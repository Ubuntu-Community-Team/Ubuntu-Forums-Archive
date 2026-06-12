---
title: "basic networking question"
date: 2007-01-29
forum: General Help
---

### Post by seshomaru samma on 2007-01-29
Whenever I bring my Dapper laptop to work , I have difficulties connecting to the net . This is probably because the LAN cable is bad (other Windows laptops seem to have to problems with that as well). If Ubuntu can't connect ,then I need to play with the cable and once the light at the LAN connection at the back of the laptop turns on ,I know it's OK .But then I need to reboot the laptop in order for it to connect to the internet.

But in my friends' XP laptop reboot is not needed, you play with the cable a bit and then when you get the right position the little light turns on in the LAN connection and XP finds the connection automatically.
I'm sure Ubuntu can do that as well.but how?
Basically I find that if there was no connection at boot ,it needs to reboot in order for it to connect.
The only command I know is ifconfig
can anyone tell me how to make it look for a connection with the terminal ,without rebooting.

I hope my explanation makes sense....:confused:

---

### Post by kingmonkey on 2007-01-29
```
sudo /etc/init.d/networking restart 
```

---

### Post by p!=f on 2007-01-29
> **seshomaru samma said:**
> Whenever I bring my Dapper laptop to work , I have difficulties connecting to the net . This is probably because the LAN cable is bad (other Windows laptops seem to have to problems with that as well). If Ubuntu can't connect ,then I need to play with the cable and once the light at the LAN connection at the back of the laptop turns on ,I know it's OK .But then I need to reboot the laptop in order for it to connect to the internet.

But in my friends' XP laptop reboot is not needed, you play with the cable a bit and then when you get the right position the little light turns on in the LAN connection and XP finds the connection automatically.
I'm sure Ubuntu can do that as well.but how?
Basically I find that if there was no connection at boot ,it needs to reboot in order for it to connect.
The only command I know is ifconfig
can anyone tell me how to make it look for a connection with the terminal ,without rebooting.

I hope my explanation makes sense....:confused:
To restart networking type
```

sudo /etc/init.d/networking restart

```
or you might want to install network-manager-gnome for... yes, GNOME :) or knetworkmanager for KDE to automatically take care of your connection.
Btw, why not to make a new cable or repair the current one? :)

---

### Post by seshomaru samma on 2007-01-29
> **p!=f said:**
> 
Btw, why not to make a new cable or repair the current one? :)

thanks for the answer
I took care of the cable ,but I wanted to learn in case I ever needed to use that command.

BTW- how do I run network-manager-gnome?

---

### Post by p!=f on 2007-01-29
> **seshomaru samma said:**
> 
BTW- how do I run network-manager-gnome?
On Feisty here it added itself automagically to Sessions -> Startup Programs as Network Manager.
```

nm-applet

```

---

