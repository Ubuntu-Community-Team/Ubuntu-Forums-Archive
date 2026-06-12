---
title: "Daemons"
date: 2006-12-21
forum: General Help
---

### Post by Dr Small on 2006-12-21
Hi.
I need some help with daemons that run at startup.
Everytime I reboot my pc, tor will run, and I have to stop it, and I want xampp to start, so I have to start it.

Here's the commands I have to type after bootup to get what I want:
```

sudo /etc/init.d/tor stop
```
and
```
/opt/lampp/lampp start
```

If there was some way to make the daemon tor not run at reboot, and make it so xampp (lampp) starts at reboot, it would make my life easier. :)

Any help would be appreciated.
Dr Small

---

### Post by gaebriel on 2006-12-21
Two options for you: 

1) you can check to see if the services are controllable through `services-admin`, and just check the boxes for services you want to start on boot, or uncheck the boxes for services you don't want to start on boot. 

2) Modify the S* and K* shortcuts within the /etc/rc3.d and /etc/rc5.d directories manually. If you're booting up using X-windows, as I assume you are, then you'll want to modify the /etc/rc5.d directory entries. 

The basic premise is, anything you want to startup on a particular runtime level (1, 2 - single-user, 3 - standard no X, 4, 5 - X) needs to have a shortcut to the real service script located in /etc/init.d. The syntax of the shortcut is [S][K]NUMBER where "S" tells the service to start on boot, "K" tells the service to stop on shutdown/reboot, and "NUMBER" tells the system which order to start or stop the service in. For each runtime level, you should add both an S and K entry so that the system can start and stop services appropriately. 

All you really need is an "S" entry for lampp within /etc/rc5.d so that the service starts on boot, and remove the "S" entry for tor so it doesn't start on boot. 

HTH

P.S.
You can find `services-admin` by going to the System menu, then click Administration, then click Services; or you can run it from a terminal window. 
You can create the shortcut to lampp by running: ln -s /opt/lampp/lampp /etc/rc5.d/S50lampp

---

### Post by christhemonkey on 2006-12-21
For your particular example, i would recommend using update-rc.d for ease of use.

To place the script in the correct place;
```
sudo ln -s /opt/lampp/lampp /etc/init.d/lampp 
```

Then to add it to boot up scripts;
```
sudo update-rc.d lampp defaults 
```


Then also to remove tor from bootup scripts:
```
sudo update-rc.d -f  tor remove 
```

This should start lampp at bootup, stop it at shutdown, and prevent tor from autostarting.

---

### Post by Dr Small on 2006-12-21
Thank! You guys are great!
My problem is fixed, and now I am happy :)

Dr Small

---

