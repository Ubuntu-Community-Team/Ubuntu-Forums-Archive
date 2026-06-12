---
title: "Apache Problem"
date: 2007-07-07
forum: General Help
---

### Post by tj71587 on 2007-07-07
I initially installed apache2 php and mysql when i first setup my computer, and now i want to put blue dragon on there as well...

I followed this guide

[http://ajlcom.instantspot.com/blog/index.cfm/2007/4/16/BlueDragon-7-JX-and-Apache-22-on-Ubuntu-Feisty-704](http://ajlcom.instantspot.com/blog/index.cfm/2007/4/16/BlueDragon-7-JX-and-Apache-22-on-Ubuntu-Feisty-704)

after uninstalling my initial apache install, I went to start the new apache install and get...

httpd: Could not reliably determine the server's fully qualified domain name, using server1.networkserver.com for ServerName
(9Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Also, I double checked that my initial one was uninstalled, and it said it was, but I can still go to localhost and get the old directory telling me that its apache 2.2.3 and not the 2.2.4 that i just installed

I didnt pay much mind and went to run the BlueDragon software and get this back.
sudo: /home/tj/Desktop/BlueDragon_Server_JX_70_339-Linux.sh: command not found

I know this is a difficult problem any help would be appreciated. I am fresh out of ideas.

---

### Post by dfreer on 2007-07-07
What's your /etc/hostname and /etc/hosts files look like?

I'd wait on doing the below until you post your files here:
Most likely you will just need to modify the following line in /etc/hosts:
```
127.0.0.1       localhost
```

to:
```
127.0.0.1       localhost.localdomain    localhost
```

That's off the top of my head.

EDIT: Furthermore, this is only going to resolve the "Could not determine the FQDN" error, dunno if I can help with trying to get BlueDragon installed.

---

### Post by tj71587 on 2007-07-07
My hostname file says

```
server1.networkserver.com
```

My host file says

```

127.0.0.1     localhost
127.0.1.1     ubuntu
192.168.0.100    server1.networkserver.com

```

I believe I set these up when I was initially setting up apache, and they worked well enough, the only problem is that apache that i want to uninstall is still there, as well as php, which i uninstalled as well.  I think I am going to just have to reformat this unless anyone comes up with something as to completely remove apache 2.2.3.  Do I have to manually go in and get rid of every apache2 file, if so would someone mind telling me where to begin with that?

---

### Post by dfreer on 2007-07-07
You can go ahead and modify the line I mentioned, see if that will clear up the FQDN problem. Make sure to change it verbatim, don't add your servername in place of localhost.

Beyond that, the best way to completely remove a program is to do an apt-get remove --purge when uninstalling, as that should get rid of all of the configuration files. You will still need to remove any custom-made files, so if you are doing a clean uninstall of apache2 you can try this:
```
sudo apt-get remove --purge apache2
sudo rm -Rv /etc/apache2/
```

Of course, if you built your source and installed it already, this will most likely break the new apache. Just reinstall it using whatever method you used to compile & install it before, and you should be ok. Then again, I don't really know about this BlueDragon software, but hopefully this will help you out some.

EDIT:
(9Address already in use: make_sock: could not bind to address 0.0.0.0:80
Sounds like apache (either your custom or the default *.deb) is still listening. Try a reboot after you uninstall it, and then check your process list and make sure it is no longer running.

---

### Post by pbaumgar on 2007-07-07
> **tj71587 said:**
> I initially installed apache2 php and mysql when i first setup my computer, and now i want to put blue dragon on there as well...

I followed this guide

[http://ajlcom.instantspot.com/blog/index.cfm/2007/4/16/BlueDragon-7-JX-and-Apache-22-on-Ubuntu-Feisty-704](http://ajlcom.instantspot.com/blog/index.cfm/2007/4/16/BlueDragon-7-JX-and-Apache-22-on-Ubuntu-Feisty-704)

after uninstalling my initial apache install, I went to start the new apache install and get...

httpd: Could not reliably determine the server's fully qualified domain name, using server1.networkserver.com for ServerName
(9Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Also, I double checked that my initial one was uninstalled, and it said it was, but I can still go to localhost and get the old directory telling me that its apache 2.2.3 and not the 2.2.4 that i just installed

I didnt pay much mind and went to run the BlueDragon software and get this back.
sudo: /home/tj/Desktop/BlueDragon_Server_JX_70_339-Linux.sh: command not found

I know this is a difficult problem any help would be appreciated. I am fresh out of ideas.

What does you httpd.conf file look like?  The FQDN problem is most likely an issue with it; not your /etc/hosts file.

---

### Post by tj71587 on 2007-07-07
Thanks to everyone for the help, I have apache working with BlueDragon.  Now does anyone know how I would install php5 and mysql in the new directory (/usr/local/apache2/htdocs/)?

---

