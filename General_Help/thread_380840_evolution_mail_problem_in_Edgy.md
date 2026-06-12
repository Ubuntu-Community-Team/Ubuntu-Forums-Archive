---
title: "evolution mail problem in Edgy"
date: 2007-03-10
forum: General Help
---

### Post by Buster95 on 2007-03-10
First try with Evolution 2.8.1, everything went OK. Mail loaded and mail got sent.
Next time, the system can't see my ISP to fetch mail.
Re-started it in a terminal and got this:

xx@laptop:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.8:6506): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:6506): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.8:6506): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:6506): DEBUG: mailto URL program: evolution

I don't understand these messages. Can anyone help to de-cipher them?
Thanks

---

### Post by pandu.rs on 2007-03-10
kill all evolution processes before starting evolution again.

---

### Post by bapoumba on 2007-03-10
Hello, please update/upgrade your system:
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Buster95 on 2007-03-10
> **pandu.rs said:**
> kill all evolution processes before starting evolution again.
Thank you pandu.rs
Tried that - no luck.
Cheers

---

### Post by Buster95 on 2007-03-10
> **bapoumba said:**
> Hello, please update/upgrade your system:
```
sudo aptitude update
sudo aptitude upgrade
```
Thanks Bapoumba
Looks like I have another problem as well. Update doesn't run

xx@laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_AU                                    
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_AU                             
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_AU                              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_AU                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_AU                                
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_AU                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/multiverse Translation-en_AU                              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_AU                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)]

Any advice?
Cheers

---

### Post by bapoumba on 2007-03-11
What DNS are you using ?
```
cat /etc/resolv.conf
```

---

### Post by Buster95 on 2007-03-11
> **bapoumba said:**
> What DNS are you using ?
```
cat /etc/resolv.conf
```

Thanks for your interest bapoumba,

xx@laptop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 192.168.0.1
xx@laptop:~$ 

I confirmed these DMS settings with my ISP.

I have no problem with getting web pages with Firefox. I use a D-Link DL524 wireless router connected to an Netcomm NB5 ADSL2+ modem. I used "default" as the  wireless router ESSID and the connection setting is "automatic DHCP". Also, I had to blacklist ipv6 to get a web page.
Cheers

---

### Post by bapoumba on 2007-03-12
> **Buster95 said:**
> Thanks for your interest bapoumba,

xx@laptop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 192.168.0.1
xx@laptop:~$ 

I confirmed these DMS settings with my ISP.

I have no problem with getting web pages with Firefox. I use a D-Link DL524 wireless router connected to an Netcomm NB5 ADSL2+ modem. I used "default" as the  wireless router ESSID and the connection setting is "automatic DHCP". Also, I had to blacklist ipv6 to get a web page.
Cheers
Hello,
sorry just to throw links at you, but I'm on a rush at work.
This is an issue with D-Link router, please check:
[http://www.mepis.org/node/10306]("http://www.mepis.org/node/10306") for a firmware update
[http://ubuntuforums.org/showthread.php?t=381614]("http://ubuntuforums.org/showthread.php?t=381614") for the "prepend" line in /etc/dhcp3/dhclient.conf (you probably will have to adjust the DNS).

I'll check again on this later today.
Cheers.

---

### Post by Kateikyoushi on 2007-03-12
Same problem I faced yesterday.

This is what worked in that case.

> Step 1) gksudo gedit /etc/resolv.conf add the IP to your ISP if you know them or to OpenDNS (208.67.222.222 and 208.67.220.220). Like "nameserver 208.67.222.222" add one line per server, a maximum of 3 servers. There should already be one IP there, use it as a pattern. Without step 2 this is useless. 

Step 2) gksudo gedit /etc/dhcp3/dhclient.conf 

add a line "prepend domain-name-servers 208.67.222.222,208.67.220.220;" (no quotes) The DNS servers here must be the same as in /etc/resolv.conf. The prepend stops the servers being ditched in etc/resolv.conf

---

### Post by Buster95 on 2007-03-12
Thank you,
The change of DNS sugested in one of hose threads worked. I can now update and Evolution kicked in as well.
Cheers

---

