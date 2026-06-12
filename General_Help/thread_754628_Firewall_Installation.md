---
title: "Firewall Installation"
date: 2008-04-14
forum: General Help
---

### Post by Reg Editor on 2008-04-14
Hello,I'm trying to install Lokkit.I've downloaded gnome-lokkit-0.43.tar.gz and put it in the Home Folder.

owner@owner-desktop:~$ sudo apt-get install gnome-lokkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-lokkit
owner@owner-desktop:~$ 

What do I need to do?

Thank you.

---

### Post by wormser on 2008-04-14
Ubuntu has a firewall installed by default.  I have never used lokkit.  Most suggestions on this forum are to install Firestarter to manage the firewall.  

That apt-get error makes me believe you do not have the repositories open.  System> Administration> Software Sources and check Main, Universe, Multiverse and uncheck CDrom.  Then run the apt-get command like you had or for Firestarter.  Read the following link.  It will help you to understand installing software.

[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by PmDematagoda on 2008-04-14
If you want to install the program using the tar.gz file then you would have to compile it manually.

1) Extract the contents of the archive.

2) Move to the folder containing the extracted files and execute:-
```
./configure
```

3) After ./configure is done, execute:-
```
make
```
and
```
sudo make install
```
successively.

You should then be able to use it.

But if you want an easier way of doing this you can use the repositories, but it seems that you do not have the required repos activated, go to Software Sources in System>Administration>Software Sources and then select all the options in the Ubuntu Software tab and then reload the sources list as instructed, then try running the command:-
```
sudo apt-get install gnome-lokkit
```

---

### Post by Reg Editor on 2008-04-15
Thanks for your replies.For the past few days I haven't been able to connect to the internet with Ubuntu.That's with a Winmodem.

When I've solved that,I'll get back to the firewall installation.

---

### Post by Reg Editor on 2008-04-19
Under software sources I ticked the boxes for Ubuntu software and third party software,then used the command: sudo apt-get install gnome-lokkit

It worked.

How can I uninstall Lokkit so that I can install it using the method suggested by
PmDematagoda ? I'm new to Linux and want to  try to learn by experimenting.

Thanks for your help

---

### Post by PmDematagoda on 2008-04-19
> **Reg Editor said:**
> Under software sources I ticked the boxes for Ubuntu software and third party software,then used the command: sudo apt-get install gnome-lokkit

It worked.

How can I uninstall Lokkit so that I can install it using the method suggested by
PmDematagoda ? I'm new to Linux and want to  try to learn by experimenting.

Thanks for your help

Since you used apt-get to install lokkit, there isn't much of a requirement that you compile manually, but if you still want to then remove lokkit using:-
```
sudo apt-get remove gnome-lokkit
```

---

### Post by ramjet_1953 on 2008-04-19
A few of questions, if I may?

1. Are you aware that Ubuntu, and any other Linux distro already comes pre-installed with a firewall? It's called iptables.

2. Are you aware that Lokkit, Firestarter and other such programs ARE NOT firewalls, but are GUI's for iptables?

3. Are you aware that iptables comes pre-configured and ALL PORTS are closed by default and your system is secure?

4. Are you aware that there is NO NEED to touch iptables, unless you need to do any port forwarding, or your system is being used as a server?

5. Are you aware that if you want to run any of the GUI's for iptables all of the time that it is a serious security risk, as you are running a program in root mode on your desktop?

If you access the internet via an ADSL router, you also have a hardware firewall, as well.

A word of advice. Unless you need to do any port forwarding, don't try to fix something that isn't broken.

Regards,
Roger :cool:

---

### Post by Reg Editor on 2008-04-19
Thanks.I wasn't aware of any of those.

I've just been to Shields Up,ports 445 and 439 are stealth,the others up to 1055 are closed.

Is it safer for all the ports to be stealthed?

Solicited TCP Packets: RECEIVED (FAILED) &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.



Unsolicited Packets: PASSED &#8212; No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)



Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

---

### Post by ramjet_1953 on 2008-04-19
Don't forget that if you are behind an ADSL router, the results that Shields-Up gives you are for the ADSL router's firewall, not iptables.

However, your system looks safe. Just because a port is closed and not stealthed, doesn't make it any less secure.

However, you may want to go into your router's firewall settings and turn off ping reply.

Regards,
Roger :cool:

---

### Post by Reg Editor on 2008-04-20
I'm using a USB ADSL modem. :)



I've been to Shields Up again.All the 1056 ports are stealthed except for 0 and 1,they're are closed.

Why aren't they stealthed?

Now I have uninstalled Lokkit,and tried to install it with the commands.

owner@owner-desktop:~/Desktop/Lokkit-0.43$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gnome-config... no
checking for gnomeConf.sh file in /usr/local/lib... not found
configure: error: Could not find the gnomeConf.sh file that is generated by gnome-libs install
owner@owner-desktop:~/Desktop/Lokkit-0.43$ 

What needs to be done?

Thank you.

---

