---
title: "[SOLVED] Problem with hostname:-/"
date: 2008-05-19
forum: General Help
---

### Post by _sAm_ on 2008-05-19
There is 4 pc in my house, 2 are running Ubuntu and 2 are running Vista. 

I can ping both Ubuntu pc from the Vista pc, I can both ping and use nmap from one of the Ubuntu pc to the other Ubuntu pc, but not the other way around. 

So, my Ubuntu desktop can ping and use namp to my Ubuntu server, but when I try to ping the Ubuntu desktop from the Ubuntu server I get « unknow host». If I change the hostname to the local IP it will go ok. Both ssh, nfs and samaba is working fine when I use the local IP to my dekstop Ubuntu, but I want to use the hostname since the local IP change from time to time(so I need to change the nfs server).

I have checkd both /etc/init.d/hostname.sh. and /etc/hosts so I am using the correct hostname. 

Both are running Ubuntu 8.04(I had no problem with this using 7.10)

How can I fix this?

Thanks for any help

---

### Post by HalPomeranz on 2008-05-19
Would you mind posting the contents of your /etc/hosts file?  Perhaps there's a syntax error there?  Also, if you wouldn't mind supplying the output from your non-working ping command, that might also be helpful.

---

### Post by _sAm_ on 2008-05-19
....

---

### Post by HalPomeranz on 2008-05-19
Heh, you gave me everything I need except the hosts file from the machine samserver, which is where you're actually having the problem with ping.  Anyway, my guess is that you don't have an /etc/hosts entry on samserver that tells it what IP address sambuntu is using.  The problem is you'll have to change this entry every time the IP address of sambuntu changes.

OTOH, you don't have an /etc/hosts entry on sambuntu for samserver and yet it's able to find samserver just fine.  Is something in your environment acting as a DNS server?  Maybe your wireless router or one of the machines on the network?  One way to check would be to look at your /etc/resolv.conf file on sambuntu-- there should be one or more "nameserver" configuration lines in there that will tell you what IP address(es) it's using for DNS.

If you do have a local DNS server, then what you probably want to do instead of making an /etc/hosts entry is to update your DNS configs so that all of the machines on your network will know the IP address for sambuntu.  How you do that depends on what platform the DNS server is running on-- for example, configuring DNS on a wireless router is totally different from configuring DNS on a Linux box.

---

### Post by Iowan on 2008-05-19
Check post#6 in [this]("http://ubuntuforums.org/showthread.php?t=789444") thread.

---

### Post by _sAm_ on 2008-05-20
...

---

### Post by HalPomeranz on 2008-05-20
I admit to being somewhat stumped on this.  Your resolv.conf files indicate you're using 10.0.0.1 as your name server (I'm guessing this is the lan address of your router) and you don't have any /etc/hosts entries for the machines you're pinging so that means the name resolution must be coming from DNS-- at least on sambuntu where the ping actually works.  We can test that theory by running the command "host samserver" on sambuntu-- this will do a DNS lookup.  You might also try doing "host sambuntu" on samserver.

The question is why would this work on one machine and not the other?  And why would it have stopped working when you upgraded to 8.04?  Some sort of dynamic DNS update that's not happening in Hardy?  It's a strange problem to me...

---

### Post by _sAm_ on 2008-05-21
...

---

### Post by Gunman1982 on 2008-05-21
Mhh maybe a related problem to this?
[http://ubuntuforums.org/showthread.php?t=789444]("http://ubuntuforums.org/showthread.php?t=789444")
Do you have sambaclient installed on the ubuntu server?

---

### Post by _sAm_ on 2008-05-21
> **Gunman1982 said:**
> Mhh maybe a related problem to this?
[http://ubuntuforums.org/showthread.php?t=789444]("http://ubuntuforums.org/showthread.php?t=789444")
Do you have sambaclient installed on the ubuntu server?

I have installed samba and smbfs on the server, and not sambaclient(just as when I used Ubuntu 7.10 and the hostname worked).

---

### Post by Gunman1982 on 2008-05-21
And if you try to install it too?

---

### Post by _sAm_ on 2008-05-21
> **Gunman1982 said:**
> And if you try to install it too?

:)
I installed smbclient on the server, and "edited /etc/nsswitch.conf to include "wins" under the "hosts:" line" as explained in the link you gave me. But this didn't change anything - could not ping my desktop by its hostname. Then I installed winbind and now it WORKS:) :) :) 


But I don't understand why I had to do this now, and not before? Last time I used aptitude to install, but now I used apt-get - could aptitude also grab the winbind?


Thanks for all the help!

---

