---
title: "how to Acess web app from network"
date: 2008-04-23
forum: General Help
---

### Post by jagdishrao on 2008-04-23
hi guys

i am on acer 4710 Laptop with ubuntu gutsy gibbon on it.
i am a rails developer and am running a mongrel webserver
(a web server for ruby on rails platform) on port no 3000.

while the server is running i am able to acces the app with url
[http://localhost:3000/](http://localhost:3000/) and it works fine
but
when other people on network want to test the application
using the url [http://192.167.0.67:3000/](http://192.167.0.67:3000/)
where 192.168.0.67 is my laptop's ip
firefox does not show the page and throws a error

Unable to connect
firefox can't establish a connection to the server at 192.168.0.67:3000.
i tried ping 192.167.0.67 command from their pc (network) and its 
working fine.i get a reply from my laptop when i ping from any pc on network

strangely there some other ubuntu and windows development machines
on which when we access the apps with the url format
[http://ip_address:](http://ip_address:) port_no/
it works fine

pls help me
what setting i need to set for other people on network to be able to
access my web app
FYI : i have sshd(ssh server) and smbd(samba server) installed and running as service.

Regards
Jags

---

### Post by Nepherte on 2008-04-23
You should adjust your firewall settings to allow incoming connections on port 80. An easy graphical front-end  for your firewall is firestarter. To install it:
```
sudo apt-get install firestarter
```
Afterwards you can access firestarter by navigating to system > administration > firestarter

---

### Post by ryanhaigh on 2008-04-23
You shouldn't need to use adjust firewall settings unless you have previously set one up, I would check the configuration for the mongrel server, perhaps you need to edit a configuration file to enable external access or access from all network interfaces. Finally perhaps if mongrel is started before your network is configured (by newtwork manager in your system tray) it is unaware of the other interfaces and won't respond to requests from there, restarting mongrel after your network has been configured may avoid this. I have not used mongrel so I can't offer more specific advice other than to check the documentation [click here to install the docs if you haven't already](apt://mongrel-doc).

---

### Post by jagdishrao on 2008-04-24
here's the solution

sudo netstat -lnp 
showed port 3000 is binded to 127.0.0.1
i am using aptana ide for ror development and when u create a 
mongrel server instance it defaults to 127.0.0.1 as host parameter.

changed it to 0.0.0.0 and it worked

thanks again guys 
jags

---

