---
title: "command at startup"
date: 2007-04-04
forum: General Help
---

### Post by gouche on 2007-04-04
Hey everyone.

Is there a way to run a command from the terminal at startup?
At the moment, I have to put:
```
sudo iwconfig wlan0 key open **********
```
into the terminal at startup to connect to my wireless router. 

I'm guessing use some kind of script but I'm a bit of a noob and don't really know where to start.<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by kpkeerthi on 2007-04-04
Here is a straight answer to your question:

```

1. gksudo gedit /usr/bin/start-wireless
2. Add the below line to the file 
    sudo iwconfig wlan0 key open **********
3. Save and exit
4. sudo chmod u+x /usr/bin/start-wireless
5. From GNOME panel choose Preferences => Session => Startup Programs and add start-wireless to the list.
6. Log out and log back in.

```

Here is a much better solution to manage your wireless:
1. sudo aptitude update
2. sudo aptitude install network-manager network-manager-gnome wpasupplicant 
3. sudo cp /etc/network/interfaces /etc/network/interfaces.backup
4. gksudo gedit /etc/network/interfaces
5. Leave the below lines and remove the rest. Your file should now look something like:
```

   auto lo
   iface lo inet loopback

```
6. Save and exit
7. Reboot

You should now see a new networking icon in your tray. Left click and now you should be able to select your wireless access point. When prompted enter your WEP key or WPA password.

---

### Post by gouche on 2007-04-04
Cool, cheers man, that did it!

Is there any way to change the ip address with network manager?
It seems to just give me the default 192.168.1.2?

---

