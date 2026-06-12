---
title: "Ubuntu 12.04LTS, Very slow when sending password, and mail-problem"
date: 2014-03-01
forum: General Help
---

### Post by alis5 on 2014-03-01
Hello,

I'm having some strange problem with my ubuntu 12.04LTS. 
When I'm connecting to it (through a terminal), and after typing the password, it takes a very long time to log in (up to a minute). (it takes 10-20sec after pressing enter when I have typed the username, until I can start typing the password).
Same as when I'm logged in, and using sudo. If I then need to type password, it takes 10-20 seconds before anything happens.

I'm trying to set up a mailserver (with postfix and Zarafa), but this will not work either. And Iäm guessing that these 2 things are related.
Here I can't get my mails from postfix to amavis/mysql, (clamav and spamassassin is off).

I think it's something wrong with the DNS (related to localhost) or the authentication.

I have these 2 errors in my syslog:
smbd[631]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
snmpd[1589]: error on subcontainer 'ia_addr' insert (-1)
   Pluse these for the mail-problem:
CRON[23044]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
postfix/pickup[22759]: B7D6A2F80971: uid=0 from=<root>
postfix/cleanup[23051]: B7D6A2F80971: message-id=<20140301150901.B7D6A2F80971@glensoserver.glenso.so>
postfix/qmgr[1540]: B7D6A2F80971: from=<root@glensoserver.glenso.so>, size=852, nrcpt=1 (queue active)
postfix/smtp[23053]: B7D6A2F80971: to=<root@glensoserver.glenso.so>, orig_to=<root>, relay=smtp.bredband.net[195.54.106.231]:25, delay=25, delays=0.11/0.01/25/0.3, dsn=2.0.0, status=sent (250 ok:  Message 525837608 accepted)
postfix/qmgr[1540]: B7D6A2F80971: removed

This is my hosts file:
127.0.0.1       localhost
127.0.0.1       localhost.localdomain localhost
127.0.1.1       glenso
192.168.0.100   glensoserver.glenso.so
192.168.0.100   glensoserver.glenso.so glensoserver

and in nsswitch.conf I have:
hosts: files dns
shadow: files ldap
rpc: db files
services: db files
networks: files
passwd: files ldap
netgroup: nis
group: files ldap
protocols: db files
ethers: db files

And in postfix (for my mail-problem), (a small cutout):
inet_interfaces = all
mydestination = localhost
mynetworks = [::1]/128, [::ffff:127.0.0.0]/104, 127.0.0.0/8, 192.168.0.0/24, 192.168.0.100
mailbox_transport = zarafa
virtual_mailbox_domains = glenso.so
virtual_mailbox_maps = ldap:/etc/postfix/ldap-users.cf
virtual_alias_maps = regexp:/etc/postfix/virtual_users_global, ldap:/etc/postfix/ldap-aliases.cf, hash:/etc/postfix/ldap-group.cf
virtual_transport = lmtp:127.0.0.1:2003
content_filter = smtp-amavis:[127.0.0.1]:10024
myhostname = glensoserver.glenso.so

Anyone that has any ideas of what could be causing this?
I'm out of ideas, (and so seems google to be for me as well...)

---

### Post by r.stiltskin on 2014-03-01
You seem to have some conflicting info in /etc/hosts.  Try commenting out the extraneous lines and modify 127.0.1.1 entry to include the domain name [edit: and correct the hostname on this line as well]:

```

127.0.0.1 localhost
# 127.0.0.1 localhost.localdomain localhost
127.0.1.1 glensoserver.glenso.so glensoserver

#192.168.0.100 glensoserver.glenso.so
192.168.0.100 glensoserver.glenso.so glensoserver

```

---

### Post by alis5 on 2014-03-01
Thanks for the help, but unfortunatly that didn't help. Still the same problem... :(

---

### Post by r.stiltskin on 2014-03-01
It just occurred to me that you should also check the contents of /etc/hostname.

The entry in that file should agree with whatever you have as hostname in /etc/hosts.  In the example in my post #3, the hostname is glensoserver, the domain is glenso.so and the "fully qualified domain name" is the hostname+domain, i.e., glensoserver.glenso.so.

Note that in your original /etc/hostname file, you had the hostname as glenso on the third line and glensoserver on the last line.

Also, I'm not sure but if you make any changes to the hosts or hostname files, it may be necessary to reboot in order for them to take effect (although it might be sufficient to disable networking and then enable it again.

And in any case, /etc/hosts should not have multiple lines with the same ip address -- that's why I suggested commenting out those 2 lines.

---

### Post by alis5 on 2014-03-01
In my /etc/hostname I have "glensoserver". Thats it.
In my hosts I now have:
127.0.0.1 localhost
127.0.1.1 glensoserver.glenso.so glensoserver
192.168.0.100 glensoserver.glenso.so glensoserver

But still no change. 

I always reboot the server, then I also see direct if the fix works or not (when I login).

And thanks alot for the help! 
I'm not so good at Linux and I have searched the web for 3 week (for a solution), and haven't got this thing to work. It's really bugging me...

---

### Post by r.stiltskin on 2014-03-01
Please describe your setup more clearly.  Are we talking about a command-line only (no GUI desktop at all) Ubuntu Server and ssh login from another machine in your local network, or login on a keyboard & monitor attached directly to the server, or something else?

---

### Post by alis5 on 2014-03-02
It's a no GUI desktop, where I login in with SSH (usually from my internally network).
The main thing for this server is to run samba (so I can access my data  from all computer in my house), and to us it as a mailserver (Zarafa  with yaffas). But also for torrent, and DLNA. Everything exept the mail  is working.

When I was working with putting zarafa up and running, the DNS suddenly  stoped working, (I couldn't connect to my smtp address, but after  changeing the resolv.conf I got it to work again). I don't remeber  exactly how I did it, but I had to change some more file to get it to  "stick".
Here is my resolv.conf:
nameserver 203.67.222.222
nameserver 203.67.220.220
nameserver 8.8.8.8

---

### Post by alis5 on 2014-03-04
No one that has any more suggestions?

---

### Post by r.stiltskin on 2014-03-04
What is the lan ip address of your router? (192.168.0.1 ?)

Also, please post the contents of /etc/network/interfaces.

---

### Post by alis5 on 2014-03-05
Yes, the router has IP: 192.168.0.1.

And this is my output of /etc/network/interfaces:

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1
auto lo
iface lo inet static
        address 127.0.0.1
        netmask 255.255.255.0

---

### Post by steeldriver on 2014-03-05
The default /etc/nsswitch.conf on both my 12.04 boxes (one Desktop, one Server) has

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

IIRC, if you are connecting via SSH from Windows, another cause for slow login can be that it is busily attempting GSSAPI authentication - so you may want to disable that in the server's /etc/ssh/sshd_config:

```

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

```

---

### Post by alis5 on 2014-03-05
Thanks for the help!

This is my nsswitch.conf:
hosts: files dns
shadow: files ldap
rpc: db files
services: db files
networks: files
passwd: files ldap
netgroup: nis
group: files ldap
protocols: db files
ethers: db files



And this is my sshd_config:
Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


And yes, I'm connecting from windows 7. (SSH and putty).

---

### Post by alis5 on 2014-03-05
Tried to uncomment the last to line in ssh_config, and also tried to set "GSSAPIAuthentication no". I rebooted the server bewteen each change. But still the same ting. Still very slow.

---

### Post by r.stiltskin on 2014-03-05
I would suggest that you revise these two files as follows.  This is the way the Ubuntu installers are configuring these files, and it seems to work perfectly for me.  You might want to keep backup copies of the old versions (rename them with a .old extension) "just in case".


/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.0.100
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    dns-nameservers 192.168.0.1
    dns-search glenso.so

```

/etc/resolv.conf:
```

nameserver 192.168.0.1
search glenso.so

```

---

### Post by r.stiltskin on 2014-03-05
By the way, after making all of these various changes it is probably a good idea to reconfigure postfix.  Run:
```
dpkg-reconfigure postfix
```

I can't help with Zarafa -- I know absolutely nothing about that.

---

### Post by alis5 on 2014-03-06
Thanks that did it! :KS

Now my login (and sudo) works as it should!

I still have problems with my mail, but that's for another thread. :-)

Once again, thank's alot for the help!!!

---

