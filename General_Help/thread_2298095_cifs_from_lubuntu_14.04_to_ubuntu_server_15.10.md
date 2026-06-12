---
title: "cifs from lubuntu 14.04 to ubuntu server 15.10"
date: 2015-10-09
forum: General Help
---

### Post by sparky-steve on 2015-10-09
Hello!

I just changed my server from lubuntu 14.04 to ubuntu 15.10 server.

The following code was working on lubuntu:

```

mount -t cifs -o username=user@domain.com,password=MyPassword //192.168.10.21/Users/username/directory /root/scripts/tmp/

```

But now, on the new server I get this error

> Unable to find suitable address.

I assume there's some notable changes between smb/cifs on lubuntu and ubuntu....

Any help or pointers gratefully received!

SS

---

### Post by nerdtron on 2015-10-09
I'm not sure what checks have you done already but here are some pointers:

Did the IP of the server changed?
Is the Samba service from the server running? ( I think 192.168.10.21 is a windows machine? )
Does the firewall from the server blocks smb ports?
Try to use "mount -v" to see the mounting in verbose mode and see if there are any errors.

---

### Post by sparky-steve on 2015-10-09
Hello,

Both IP addresses have changed, but this is reflected in the command.
Yes, it's a windows machine, and it is pinging fine on the new IP address
I'm using shorewall on the server (ubuntu server 15.10, new installation as of yesterday) and there are no blocks between the firewall (server) and the local network.
mount -v shows nothing more except this one line:

> mount.cifs kernel mount options: ip=192.168.10.21,unc=\\192.168.10.21\Users,user=username,prefixpath=path/to/directory,pass=********

The exact command worked yesterday morning on lubuntu 14.04

It's quite frustrating, yet experience tells me the solution will be simple!

Thanks for your input so far....

---

### Post by sparky-steve on 2015-10-09
Hold that thought!

I cleared iptables, and it worked; So you were quite right - it IS a firewall issue - and that confuses me because I have explicitly ensured there are no block/deny/drop rules between the server and the lan....

---

### Post by sparky-steve on 2015-10-09
ok.... 

dear future readers.....

Shorewall changed; SMB is blocked by default from $FW to LOC

[http://shorewall.net/samba.htm](http://shorewall.net/samba.htm)

specifically you need this in /etc/shorewall/rules:

> #ACTION   SOURCE   DEST   PROTO    DEST PORT(S)   SOURCE
#                                                 PORT(S)
SMB(ACCEPT)  $FW      loc
SMB(ACCEPT)  loc      $FW

---

