---
title: "no default gw from dhcp"
date: 2013-01-16
forum: General Help
---

### Post by stormcel on 2013-01-16
I LOVE Ubuntu, but it can be exceedingly frustrating.
I'm not even going to go into my Atheros "UNCLAIMED" issues that remain unresolved after days of following forum advice.  I've just literally given up trying to go wireless.
 
However, this should be an easy fix for any of you who know this OS.
On my working wired connection:
I have my eth0 set to dhcp in /etc/network/interfaces
it grabs an ip from the router no prob , but does not get a default gateway.
I have to 
sudo add defautl gw x.x.x.x everytime I boot.
This machine moves around to different networks, it needs to automatically grab a gateway.
I have got to be missing something.
The forums all have super complicated issue...multiple nics, networks etc.
This is a simple noob issue.
I'm not getting a gateway from dhcp.... that's it
Is there a file I need to edit or delete?
please help, I am sick of failing to fix these issues.

---

### Post by SeijiSensei on 2013-01-16
I'd check the router or DHCP server.  I'd bet the problem is there and not on your machine.

---

### Post by Warren Hill on 2013-01-16
Open a terminal (CTRL+ALT+T) what's the output of the following command?

cat /etc/network/interfaces

---

### Post by Doug S on 2013-01-16
In addition to the comments already made...
I would suggest to look at the /var/lib/dhcp/dhclient.eth0.leases file (it might be named simply /var/lib/dhcp/dhclient.leases for you). That file will contain the information returned from the DHCP server. Look for a line similar to this:```
  option routers 173.180.45.1;

```Also check your /etc/dhcp/dhclient.conf file and make sure you are asking the dhcp server for the gateway (router) information (it does by default). Look for something like:```
request subnet-mask, broadcast-address, time-offset, [COLOR=red]routers[/COLOR],
        domain-name-servers;
```

---

### Post by stormcel on 2013-01-17
You guys are great!
Thanks for all of the incredibly valuable info!!!
Unfortunately I already had to turn the box over for testing, currently I just use a bash script to add the default route as a workaround, but I am getting my hands on it in a few days and I'm going to track this down.
For those who are interested this is an Asus eeebox.
I will definitely get back to this thread to let everyone know how it goes.
And once again THANK YOU

---

### Post by stormcel on 2013-02-12
OK, I finally got back to the box and everything looks right. It is requesting router info in both files, but I still do not get a gateway.
Interestingly, when I setup a static ip with gateway in the interfaces file, I STILL do not get a gateway.
THE ONLY WAY that I seem to be able to get a gateway is with the sudo add default gw line.
hmmmmmm

---

### Post by Doug S on 2013-02-12
Well, I am at a loss. The only thing I can suggest is that you post some actual outputs and file contents. Include output from```
route -n
```for before and after you force the default gw.

---

### Post by stormcel on 2013-02-22
This box is supposed to be headless and running as basically an 'embedded' device.
That being said, I was looking for ways to configure all of the box's settings through a non-technical web interface for non-technical users. So I installed ebox to manage the ubuntu server through http.
Could ebox be responsible for the gateway issue?
I'm installing a fresh system and testing for a gateway at each step.
 
 
-------
edit
purged ebox...now have gateway
Thanks for everything guys!!!!

---

