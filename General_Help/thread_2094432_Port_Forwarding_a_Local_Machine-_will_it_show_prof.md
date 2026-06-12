---
title: "Port Forwarding a Local Machine- will it show profile login?"
date: 2012-12-13
forum: General Help
---

### Post by Stephan H on 2012-12-13
Hello forum,

Got a simple question and I thought there is a simple solution to it, but I'm not sure anymore:

I set up a port forwarding for a local machine then registered with no-ip.org and tried to access the machine from outside the LAN but it won't connect.

Question: Shouldn't this display the account login screen?


Some more details:
fixed IP via MAC filtering on the router;
DHCP on the local machine (if I specify the same fixed IP, it won't connect);
the same method works well ton get through to two IP cams;
made three user accounts plus roodadmin;
version: Kubuntu 12.04 LTS.


Stephan

---

### Post by Ms. Daisy on 2012-12-13
> **Stephan H said:**
> 
DHCP on the local machine (if I specify the same fixed IP, it won't connect);

This part makes no sense. The IP of your server must be static on your LAN. Your port forwarding won't be valid on any other IP.  Most routers allow you to do IP reservations, that would probably work.

---

### Post by jim_deadlock on 2012-12-13
no-ip.org is a DNS forwarder. Before you start messing with that you should make sure the service you're running is accessible via your external IP address. If not, then you need to fix your port forwarding, firewall (if you have one running) and the service itself. Once you can reach it via IP address and it's all working correctly, then you can set up your no-ip.org account.

---

### Post by Stephan H on 2012-12-14
> **jim_deadlock said:**
> no-ip.org is a DNS forwarder. Before you start messing with that you should make sure the service you're running is accessible via your external IP address. If not, then you need to fix your port forwarding, firewall (if you have one running) and the service itself. Once you can reach it via IP address and it's all working correctly, then you can set up your no-ip.org account.

Hi,

Well I've got no really fixed IP hence I needed a DNS forwarder.
But as I said, it works with the IP cams which is why I assume this would not be a problem...

Stephan

---

### Post by Cheesehead on 2012-12-14
Narrow the problem: 

If you can ping your server, then the problem is the server firewall, service, or port setting.

If you cannot ping your server, then the problem is yout DNS forwarder, router firewall, or port forwarding settings.

---

### Post by steeldriver on 2012-12-14
> **Stephan H said:**
> Question: Shouldn't this display the account login screen?


what do you mean exactly? are you trying to start a plain terminal session or a graphical login? what services have you enabled on the target machine and what client are you using to connect with?

---

### Post by Stephan H on 2012-12-14
> **steeldriver said:**
> what do you mean exactly? are you trying to start a plain terminal session or a graphical login? what services have you enabled on the target machine and what client are you using to connect with?

Sorry wasn't clear enough perhaps:

I created four user accounts. 
When I startup I get the KDE user login (not a terminal session) and I was wondering if this is what one would/should get when you try to access this machine from outside the LAN through a forwarded port.

Services enabled? Nothing in particular (yet).
I'd be using different machines to connect, could be Linux, Windows, Iphone etc. via http/browser.

Stephan

---

### Post by Ms. Daisy on 2012-12-14
OK, let's back up.  You need a service running on that port, listening for incoming connections in order to connect to it from a remote machine. Services like sshd would run on the home box.  Then you would use an ssh client on your remote computer to connect to it.

I think you want remote desktop. Have a look at this:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

You can install remote desktop through the software center.  It is important that you secure it properly. See the security sticky in the Security Forum for more about that.

---

### Post by Stephan H on 2012-12-15
> **Ms. Daisy said:**
> OK, let's back up.  You need a service running on that port, listening for incoming connections in order to connect to it from a remote machine. Services like sshd would run on the home box.  Then you would use an ssh client on your remote computer to connect to it.

I think you want remote desktop. Have a look at this:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

You can install remote desktop through the software center.  It is important that you secure it properly. See the security sticky in the Security Forum for more about that.


Hello,

Thanks for the info, will check all these out.
I've got Remmina remote desktop installed with which I usually connect to a local machine through a Windows small business server at work.

How comes the IP cam (Edimax 1510WG) works without any further installations?

Stephan

---

### Post by Cheesemill on 2012-12-15
> **Stephan H said:**
> How comes the IP cam (Edimax 1510WG) works without any further installations?

Because it has its own inbuilt webserver.

---

### Post by Stephan H on 2013-01-10
Right,

So I installed SSH server, configured it according to the (quite good) documentation.
One thing I did different: I did not use port 22 but a different one as I've got another one open on the router. Every time I now try to connect 
```
ssh -v localhost
``` it automatically adresses port 22 and of course returns ```
ssh: connect to host localhost port 22: Connection refused
```.
Something must be still set to address port 22 somewhere. But what is it and where can I change it?


Stephan

PS Couldn't find a firewall in 12.04 LTS. Any settings to be aware of somewhere there if it exists?

---

### Post by Cheesemill on 2013-01-10
You need to use the -p switch to specify your alternate port, for example...
```
ssh -p 22222 localhost
```

---

### Post by steeldriver on 2013-01-10
You can use the -p command line option to specify your ssh port

```
NAME
     ssh â OpenSSH SSH client (remote login program)

SYNOPSIS
     ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
         [-D [bind_address:]port] [-e escape_char] [-F configfile] [-I pkcs11]
         [-i identity_file] [-L [bind_address:]port:host:hostport]
         [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [COLOR=Blue]**[-p port]**[/COLOR]
         [-R [bind_address:]port:host:hostport] [-S ctl_path] [-W host:port]
         [-w local_tun[:remote_tun]] [user@]hostname [command]

DESCRIPTION
     ssh (SSH client) is a program for logging into a remote machine and for
     executing commands on a remote machine.  It is intended to replace rlogin
```Type 'man ssh' to get a list of all the command line options / usage

---

### Post by Stephan H on 2013-01-10
Hello,

Thanks. Most helpful. Problem solved :)

However: If I login with whatever user profile I created and authorised in the sshd_config one can always access all directories. 
This machine is meant to function as a NAS and perhaps as a proxy first of all. So made three profiles and three partitions on another HDD.
Each profile got a home directory and shuld be assigned a partition.
Access should be limited to just /home/<user> and the specific partition.

It doesn't seem that one can limit access through SSH or am I wrong?
Which other way would one make access settings?

Meanwhile I tried to login via Dolphin ```
fish://<user>@localhost
```. 
It promts for password but wouldn't connect. Would think I should mention the port here again?
If accessed from outside the LAN, would it be ```
fish://<user>@<IP or web address>:<port>
```  ?

Stephan

---

### Post by Stephan H on 2013-01-11
Update: 

Dolphin does connect now via ```
fish://<user>@<IP:port>
```.

I tried to get through to the desktop using Remmina:
- it does open the SSH terminal (secure shell option);
- VNC option: it connects, promts for password, then comes "Not a valid VNC server (SSH-2.0-Open)". Server is specified by ```
ip:port
```.
- SFTP opens the /home/<user> folder, no problem.
- VNC incoming and RDC would not apply here.

This seems to be the last step to make this local machine accessible from anywhere (apart from setting user access permissions).
Does anyone know how to make Remmina connect?

I'm using Remmina regularly to connect to a remote Windows machine through a Win Small Business Sever 2003.

Stephan

---

