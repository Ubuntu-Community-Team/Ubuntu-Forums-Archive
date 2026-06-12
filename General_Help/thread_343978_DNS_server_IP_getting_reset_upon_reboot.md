---
title: "DNS server IP getting reset upon reboot"
date: 2007-01-22
forum: General Help
---

### Post by kpkeerthi on 2007-01-22
I have specified the DNS server IP under System -> Administration -> Networking -> DNS. But it is getting reset to default upon reboot. How do I make it stick?

Default => 192.168.1.1
What I want to stick => 4.2.2.1

I had to change the DNS due the issue I posted here... [http://ubuntuforums.org/showthread.php?t=343392](http://ubuntuforums.org/showthread.php?t=343392)

---

### Post by evilghost on 2007-01-22
sudo chattr +i /etc/resolv.conf

---

### Post by kpkeerthi on 2007-01-22
Thanks... but should I really set the attribute i ( A file with the &#8216;i&#8217; attribute cannot be modified: it cannot be  deleted or  renamed,  no  link  can  be created to this file and no data can be written to the file. - from man pages) Why is the DNS name getting overwritten on reboot? May be there is something else we could do? Any ideas?

---

### Post by evilghost on 2007-01-22
If you want to modify it, delete it, rename it, mangle it, then just:

sudo chattr -i /etc/resolv.conf

If I had to guess upon reboot you get a new DHCP lease and your DHCPd is configured to hand out a different IP for DNS resolution.  If you want to do it the right way change the DNS server in your DHCP scope.

---

### Post by kpkeerthi on 2007-01-22
> If you want to do it the right way change the DNS server in your DHCP scope.
Can you please tell me how do i do it?

---

### Post by dbott67 on 2007-01-22
By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]4.2.2.1[/COLOR]**;
```

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR="Blue"]prepend domain-name-servers 4.2.2.1;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```

-Dave

---

### Post by kpkeerthi on 2007-01-22
I owe you a million thanks Dave.

---

