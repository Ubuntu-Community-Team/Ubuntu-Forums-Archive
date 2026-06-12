---
title: "Putty SSH"
date: 2005-05-04
forum: General Help
---

### Post by Thyrth on 2005-05-04
Hi,

I've set up an SSH server to connect secure from work to my home Ubuntu.
This is working great, no problems here.
But now I would like to go a step further and make an http tunnel to forward some blocked ports from work to my home ubuntu.
Actualy I would like to make a tunnel for my internet traffic for a little privacy.

Is it neccesary to install HTTPTUNNEL on Ubuntu? and to put something like 

hts 8080 --forward-port 127.0.0.1:22   ???

I'm not shure what to do or how to set this up right .... ](*,) 


[http://www.linuxsa.org.au/pipermail/linuxsa/2003-July/057962.html](http://www.linuxsa.org.au/pipermail/linuxsa/2003-July/057962.html) 
[http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)
[http://sebsauvage.net/punching/](http://sebsauvage.net/punching/)
[http://www.buzzsurf.com/surfatwork/#setup_putty](http://www.buzzsurf.com/surfatwork/#setup_putty)
[http://www.comp.nus.edu.sg/~andrews/vnc_ssh/](http://www.comp.nus.edu.sg/~andrews/vnc_ssh/)
[http://borosenclave.com/putty-ssh.php](http://borosenclave.com/putty-ssh.php)
[http://www.jfitz.com/tips/putty_config.html](http://www.jfitz.com/tips/putty_config.html)
[http://www.certaintysolutions.com/tech-advice/ssh_on_nt.html](http://www.certaintysolutions.com/tech-advice/ssh_on_nt.html)

---

### Post by defkewl on 2005-05-04
What do you want to achieve?

---

### Post by Thyrth on 2005-05-04
That the internet traffic is not logged by company proxy - but is tunneled to my linux box at home, through the proxy O:)

---

### Post by Fab on 2005-05-04
[QUOTE=Thyrth]That the internet traffic is not logged by company proxy - but is tunneled to my linux box at home O:)[/QUOTE]
 well, the connection from your work box to your home box would go over company proxy too, so i dont see where you benefit from that (except if you encrypt the traffic)

---

### Post by Thyrth on 2005-05-04
If I'm not wrong, SSH will take care of that.
So first I'm making the SSH tunnel (port 22 is not blocked here). When that is made 
I do a port foward through the tounnel with SSH encrypted...

---

### Post by mlmurray on 2005-05-04
Are you talking about, maybe running an http proxy on your home machine?  If you're able to adjust the "connection" settings on your browser, you can do this, but there is an easier way.

There are lot's of open proxies on the internet that you can use.  And, if you're using firefox, there is an extension (I think it's called "SwitchProxy Tool") that you might want to try.

Now, if that's not possible, you could run a VNC server at home and tunnel port 5901 to your work machine, then connect your VNC client to "localhost:1" and basically just do all your internetting remotely on your home computer.  Check into FreeNX for an even better and easier solution.

The normal ssh command for fowarding ports is something like this:
```
ssh -L 5901:localhost:5901 your.home.ip.com
``` This, if you want to forward port 5901 on your home machin to port 5901 on your local (work) machine.  I don't know what the equivalent setting in Putty would be.

---

### Post by Thyrth on 2005-05-04
Thanks for the reply :

I want to do the same with the proxy port so something like 

> ssh -L 8080:localhost:8080 your.home.ip.com

I also installed HTTPTUNNEL (*apt-get install httptunnel*)
But still have a little problems configuring it.
This should route the incomming port to my ISP proxy somehow

I know this is possible, but don't know exactly how to

it's something with the _hts command_ on the server site.

any ideas??

---

### Post by mlmurray on 2005-05-04
[QUOTE=Thyrth]Thanks for the reply :

I want to do the same with the proxy port so something like 



I also installed HTTPTUNNEL (*apt-get install httptunnel*)
But still have a little problems configuring it.
This should route the incomming port to my ISP proxy somehow

I know this is possible, but don't know exactly how to

it's something with the _hts command_ on the server site.

any ideas??[/QUOTE]

This will forward port 8080 on your home machine to port 8080 on your local (work) machine.  If there is a proxy at port 8080, then all you need to do is the the proxy address (in your browsers connection settings) to "localhost" and the port to 8080.  However, unless your home connection is very fast, this is going to be very slow.  I would suggest googling for a list of open proxy servers and using those.  The firefox extension I mentioned earlier will take a list of those and change proxies periodically.

I don't know anything about "hts" but ssh port forwarding works as described.

Good luck!

---

### Post by Thyrth on 2005-06-16
[FONT=Georgia][SIZE=5]**SOLLUTION :**[/SIZE][/FONT]


*open putty and fill in the connection settings

*then go to Tunnels

       source port : 4321 (for example)
       destination : proxy.skynet.be:8080 (put in your isp proxy server @ home)

* click add

* Make the connection to your SSH server @ home

* now adjust the proxy settings in IE to use 127.0.0.1:4321


And there you go, no surf history for the Boss

---

