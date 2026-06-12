---
title: "&quot;server not found&quot;"
date: 2007-12-24
forum: General Help
---

### Post by ULAMSS5 on 2007-12-24
hey guys. there are afew websites that i always went to when i was using windows xp. but when i started using ubuntu, they always said "server not found etc.etc.". i checked the spellings and everything. no errors, i even asked my friends if the web closed or something, and even asked them to send me direct links, they said they can still access it. but i still cant. but they are using windows xp/vista. is there some way to fix it?

---

### Post by cdenley on 2007-12-24
Posting this output would help
```

ping -c 1 www.brokensite.com
cat /etc/hosts
cat /etc/nsswitch.conf
cat /etc/resolv.conf
sudo iptables -L

```

Change [www.brokensite.com](www.brokensite.com) to one of the sites you cannot connect to.

---

### Post by ULAMSS5 on 2007-12-25
It didn't work. I'm supposed paste the code lines each at a time, using "terminal" right? And do i have to restart/relogin for the changes to take place?

---

### Post by zvacet on 2007-12-25
Is it problem with few sites,or you don´t have internet connection at all?

---

### Post by ULAMSS5 on 2007-12-25
its just afew, very few but important sites, anyways if i don't have internet at all how did i post here?

---

### Post by cdenley on 2007-12-25
I think you misunderstood me. I said to post the output of those commands, then someone might have an idea of what your problem is. Those commands won't fix or change anything, just gives us an idea of how your system is configured to resolve host names. It would be easier to read if you posted the output one command at a time, and yes those commands would be run in terminal.

---

### Post by zvacet on 2007-12-25
> anyways if i don't have internet at all how did i post here?

Form Windows or Mac maybe.Follow **cdenley** advice and post output of commands here and somebody will help you to solve that problem.

---

### Post by ULAMSS5 on 2007-12-26
Oh. ok. you mean like this?

larry@larry-laptop:~$ ping -c 1 ithasallended-.blogspot.com
ping: unknown host ithasallended-.blogspot.com
larry@larry-laptop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       larry-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
larry@larry-laptop:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
larry@larry-laptop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
larry@larry-laptop:~$ sudo iptables -L
[sudo] password for larry:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
larry@larry-laptop:~$

---

### Post by ~LoKe on 2007-12-26
Recent linux versions of Firefox and Opera browsers don't support hyphens as a prefix or a suffix to subdomains.  This can be seen with [http://-kol.deviantart.com](http://-kol.deviantart.com).

---

### Post by ULAMSS5 on 2007-12-26
so i have to download an older vers of firefox to be able to see it? if yes please give me the link. thanks

---

### Post by cdenley on 2007-12-26
It is technically not a valid domain name, which is why it won't be resolved in ubuntu regardless of what browser you use. The problem is that Microsoft doesn't like to follow standards. If you have trouble accessing multiple sites with a subdomain name starting or ending with a hyphen, I'm surprised you didn't notice the pattern.

[http://tools.ietf.org/html/rfc1034](http://tools.ietf.org/html/rfc1034)
> 
<subdomain> ::= <label> | <subdomain> "." <label>
<label> ::= <letter> [ [ <ldh-str> ] <let-dig> ]
...
The labels must follow the rules for ARPANET host names.  They must
start with a letter, end with a letter or digit, and have as interior
characters only letters, digits, and hyphen.


I think a work-around would be to add this line to /etc/hosts:

72.14.207.191 ithasallended-.blogspot.com

Edit it using "sudo gedit /etc/hosts".

---

### Post by ULAMSS5 on 2007-12-27
erm. can you give me the full instructions/codes to get it done? i'm kinda new at this thing.

---

### Post by tehet on 2007-12-27
[http://ithasallended-.blogspot.com/](http://ithasallended-.blogspot.com/)
doesn't work here either.

[http://ithasallended.blogspot.com/](http://ithasallended.blogspot.com/)
does.

---

### Post by cdenley on 2007-12-27
On the top-left, click "applications". Under "Accessories", click "Terminal". Copy and paste the following command, then press enter.
```
sudo bash -c "echo 72.14.207.191 ithasallended-.blogspot.com>>/etc/hosts"
```

I though adding a line with gedit was simple enough, but I can't make it much simpler than this.

Windows and Mac OSX seems to allow this invalid domain name. Ubuntu and FreeBSD won't resolve it using a DNS server.   [http://ithasallended.blogspot.com/](http://ithasallended.blogspot.com/) seems to be a different site. This isn't a bug in Ubuntu, just MS and google not following standards.

---

### Post by ULAMSS5 on 2007-12-27
thanks.

---

