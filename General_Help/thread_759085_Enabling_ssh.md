---
title: "Enabling ssh"
date: 2008-04-18
forum: General Help
---

### Post by CactusWren on 2008-04-18
Hello,

I have gutsy setup on a desktop computer, however, Ihave a need to access it from a different system. I would like to be able to use ssh to connect to the gutsy system.

When I tried this, I get a connection refused message. Is there a way to enable ssh and/or open port 22 to enable the ssh connection?

I will be needing to run an x-windows session on the remote system to work with applications on my gutsy system.

---

### Post by ibuclaw on 2008-04-18
There is a How-To found in the [Ubuntu Communitry Docs.]("https://help.ubuntu.com/community/SSHHowto")

Follow it and see if it gets you anywhere.

Also, to make sure that you are going in the right direction, install [nmap]("http://nmap.org/download.html") on your remote desktop
If you use Ubuntu on it, type in.
```
 sudo apt-get install nmap 
```
For Windows, refer to the site.

To run the app, type in this in the terminal from your remote desktop
```
 nmap -vPNA **IP.ADDRESS.OF.PC** 
```

If you've setup ssh correctly, you'll get an answer like this:
```

Host 192.168.1.4 appears to be up ... good.
Interesting ports on 192.168.1.4:
Not shown: 1713 filtered ports
PORT    STATE  SERVICE
22/tcp  open   ssh

```

Else, the scenario where you can't connect.
```

Starting Nmap 4.53 ( http://insecure.org ) at 2008-04-18 23:36 BST
All 1714 scanned ports on 192.168.1.4 are closed

```

Regards
Iain

---

### Post by keratos on 2008-04-18
is the ssh daemon installed and running ??
```

/etc/init.d/sshd status

```

---

### Post by bodhi.zazen on 2008-04-18
Hate to ask the obvious, but did you install the ssh server ?

[uwiki]SSHHowto[/uwiki]

And be sure to secure it :

[uwiki]AdvancedOpenSSH[/uwiki]

Any issues with Firewall ? Router ?

---

