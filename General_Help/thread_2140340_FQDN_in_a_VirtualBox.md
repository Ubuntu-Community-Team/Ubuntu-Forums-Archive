---
title: "FQDN in a VirtualBox?"
date: 2013-04-29
forum: General Help
---

### Post by Nikolai D. on 2013-04-29
Hi all,
so i have a Debian 6 server in a virtual box, and an xp client also in a virtual box,
now i have installed fog server on the Debian 6 server and tested pulling / pushing image of the client and it works. Using this guide: [http://www.fogproject.org/wiki/index.php/Installation_on_Debian_Lenny](http://www.fogproject.org/wiki/index.php/Installation_on_Debian_Lenny)
Then i have also installed OCS NG server on this same Debian 6 server. And it works. The windows xp ocs ng client app connected the server and the client machine is added to the OCS NG Inventory server. Using this guide:
[http://wiki.ocsinventory-ng.org/index.php/Howtos:Install_OCS_on_debian](http://wiki.ocsinventory-ng.org/index.php/Howtos:Install_OCS_on_debian)

Now the next thing or the finishing touch is to setup Teledeploy: [http://wiki.ocsinventory-ng.org/index.php/Documentation:Teledeploy](http://wiki.ocsinventory-ng.org/index.php/Documentation:Teledeploy)
And since this is the second time i setup a testing server with this kind of functionalities. And now im documenting it all at the same time. Until now the instructions are pretty much ok. But then another last thing which is little bit more tricky imho is setting up the ssl on Apache web server. Although i have pretty nice explanation here: [http://www.server-world.info/en/note?os=Debian_6.0&p=httpd&f=5](http://www.server-world.info/en/note?os=Debian_6.0&p=httpd&f=5)
i have already had once some little issues with setting it up. [http://forums.ocsinventory-ng.org/viewtopic.php?id=12020](http://forums.ocsinventory-ng.org/viewtopic.php?id=12020) Which required some little tinkering.

But now my question is. Back then i asked the admins from central administration to setup FQDN for my server at the central DNS. So i could use FQDN like its explained in the last link. But that was a server on the network. Not like this one which is in a virtual box.

So how do u work/go about FQDN server addresses in a virtual box? Can i setup it somehow in a VirtualBox's DNS settings?
Any info on this would be appreciated.

Thanks in advance,
Nikolai

---

### Post by Habitual on 2013-04-30
> **Nikolai D. said:**
> So how do u work/go about FQDN server addresses in a virtual box? Can i setup it somehow in a VirtualBox's DNS settings?
Any info on this would be appreciated.

Thanks in advance,
Nikolai

terminal > sudo vi /etc/hosts and add an entry for any and/or all hosts you need to have a FQDN for.
```
123.456.123.456 <tab>bournetoraiseshell.com<tab>btrs
```for example.

and the same thing can be done to C:\Windows\System32\drivers\etc\hosts
for the Windows client(*s) that need to know exactly where the domain is.

---

### Post by Nikolai D. on 2013-05-02
so you are saying that basically i can configure the right settings (ips and fqdns etc) in the hostfiles of the two machines and this is enough to let them talk with each other without needing to have a DNS server?

---

### Post by Nikolai D. on 2013-05-03
i have changed the hostname of the linux server to the hostname.domainname.be in the hostname config file and added the entry to the hosts file: ip fqdn hostname.
But still no luck
anyone?

---

### Post by Habitual on 2013-05-03
> **Nikolai D. said:**
> so you are saying that basically i can configure the right settings (ips and fqdns etc) in the hostfiles of the two machines and this is enough to let them talk with each other without needing to have a DNS server?
Exactly.

who said change the hostname?


```
ping my_crazy_host.com
```
ping: unknown host my_crazy_host.com

```
vi /etc/hosts
``` and add
```
91.189.94.12            my_crazy_host.com my_crazy_host
```

ping my_crazy_host.com
PING my_crazy_host.com (91.189.94.12) 56(84) bytes of data.
64 bytes from my_crazy_host.com (91.189.94.12): icmp_req=1 ttl=50 time=93.3 ms

who said change the hostname?

Sorry, I can't work with folks who can't follow direction.

good luck.

---

### Post by Nikolai D. on 2013-05-16
1 i thought that is necessary to setup the right ip and fqdn on a machine to use it properly on the network.
2 The only issue that i have now. Is that the HTTP dowload folder cannot be accessed. Because i get the client notified and if i activate the package it sees the HTTPS information file URL but not the HTTP.
Whats wrong with my HTTP access to the dowload folder? Anyone? smile
Download.log says cant find pachage.

Where in Apache do i configure access to the download folder via http?

i changed  the /etc/apache2/conf.d/ocsinventory-report.conf

################################################################################
# Deployment packages download area
#
# Alias to put Deployement package files outside Apache document root directory
#
Alias /download "/var/lib/ocsinventory-reports/download"
<Directory "/var/lib/ocsinventory-reports/download">
ALLOW from all
</Directory>

from deny to allow, and still the same

---

### Post by Nikolai D. on 2013-06-10
ok i have figured out that connection, or should i better say ssl connection / communication problen was not related to FQDN.
So FQDN networking connection / communication works in VirtualBox without problems with just using the Hosts files. So its not necesarry to have a real apart DHCP server up and running inside the INTNET VirtualBoxes virtual network.

The connection/communication issue i had was SSL/https related.
SO basically i was googling and found out that on Debian i dont have to create the SSL Certificates manually the way it is done on CentOS.
i have figured out that its all about snakeoil,
or that there actually is a default ssl certificate named snakeoil that is automagically generated when you install apache2/ssl.
so you dont have to do it manually,
located under:
/etc/ssl/certs/ssl-cert-snakeoil.pem
/etc/ssl/private/ssl-cert-snakeoil.key
and regenerated by: "$ sudo make-ssl-cert generate-default-snakeoil --force-owerwrite" script command.

thx for the help,
Nikolai

---

