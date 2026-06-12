---
title: "Help to get proftpd running: can connect but not see files"
date: 2006-11-01
forum: General Help
---

### Post by roncrump on 2006-11-01
Hi, 

I have made a mess of my system (don't ask!), so decided I would just
start from scratch as Edgy is now available.

Anyway, I thought I'd use ftp to rescue my data before reformatting
(taking the opportunity to put /home and /opt on their own
partitions at the same time) and installing from scratch.

So, I put inetd and proftpd on and played about a bit.

I can now connect using FTP from another machine, but I cannot
get a directory listing (times out), let alone download everything.

My proftpd.conf follows. Please note, I' m not bothered about having
a secure ftp system running, just being able to get the data off in the
short term. I'll back it up to a CD on the other machine then
restore it from there after installing Edgy.

I can connect to the user account but nothing else.

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Debian"
ServerType			inetd
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

#DenyFilter			\*.*/

# Suggestion for default root: allows access to home dir
DefaultRoot /home/ron

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				ron
Group				ron

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on


```

Thanks.

---

### Post by divas on 2006-11-01
It seems that you are using active ftp, which cannot pass through firewalls or NAT. That's definetly the problem if your client machine uses a firewall or it is behind a NAT server.
In this case you should use passive ftp. Note that most clients use passive ftp by default. And browsers too.
If you are not familiar with passive and active ftp have a look here:

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

To setup your server to allow passive ftp behind NAT take a look here:
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html)
or search google for "proftpd" and "passive".

The best way to test if your server works with passive ftp is the command prompt tool with the -p switch to run on passive mode:
ftp -p
open your_server_IP_address:your_port_number

Good luck!

---

### Post by roncrump on 2006-11-01
> **divas said:**
> It seems that you are using active ftp, which cannot pass through firewalls or NAT. That's definetly the problem if your client machine uses a firewall or it is behind a NAT server.
In this case you should use passive ftp. Note that most clients use passive ftp by default. And browsers too.
If you are not familiar with passive and active ftp have a look here:

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

To setup your server to allow passive ftp behind NAT take a look here:
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html)
or search google for "proftpd" and "passive".

The best way to test if your server works with passive ftp is the command prompt tool with the -p switch to run on passive mode:
ftp -p
open your_server_IP_address:your_port_number

Good luck!

Thanks for the suggestion. I will have a look at it this evening (time for work now). I am only connecting locally, but I guess my wireless router/modem acts as a NAT server.

---

### Post by roncrump on 2006-11-05
Got this working thanks - not entirely sure how as I didnt' get round to trying divas suggestions.

I was also playing with samba, and as part of this process shut down the Windows XP firewall service (nb, the firewall wasn't activated, but the service was running). Voila! Next time I tried FTP to my ubuntu box, it went fine. I can only think that this change made a difference.

---

