---
title: "Problems in resolving the Hostname"
date: 2005-04-19
forum: General Help
---

### Post by VaDor on 2005-04-19
Hi there  :) ,

I having a problem that I am not understanding very well why this happening  :???: .

I  cannot resolve  hostname  of my pc  that is Badger, examples:

**Proftpd:**

Starting ProFTPD ftp daemon:  - getaddrinfo 'Badger' error: Name or service not known
 - warning: unable to determine IP address of 'Badger'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd.conf'
.


**Sudo:**

vador@Badger:/etc$ sudo -u vador  vim
sudo: unable to lookup Badger via gethostbyname()



etc..

Anyone knows how to resolve this problem?  thanks

---

### Post by VaDor on 2005-04-19
I just resolved the problem. It was quite simples  , in the /etc/hostname  I have Badger but in the /etc/hosts  I had a diferent name for the local ip so I was having problems with the hostname.





Thks anyway ppl  \\:D/

---

### Post by andvaranaut on 2005-04-19
Open your /etc/hosts file (ie. sudo gedit /etc/hosts, for example). The first line should look like:

```
127.0.0.1 localhost.localdomain localhost Badger
```

If Badger does not appear at the end of the line (which is probably what happens), add it. Save the file, and hopefully you will get rid of the errors.

Good luck

---

