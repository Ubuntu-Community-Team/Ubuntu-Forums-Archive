---
title: "Issue with gksu/gksudo"
date: 2006-10-23
forum: General Help
---

### Post by wx_nut on 2006-10-23
Hello:

I asked this on freenode, and it was suggested I post here. 

When I am attempting to use gksu from gnome (such as when I click on "Synaptic Package Manager", update-manager, Networking, or anything that required sudo access) I get a program that opens in the task bar that says "Starting Administrative Application", it spins for a bit, and then closes. 

I have attempted to apt-get remove sudo, and then apt-get install sudo.  No change.  I have also checked my sudoers file, and gksu.conf file - neither has been modified in quite some time.  Also performed a apt-get remove gksu, and apt-get install gksu.  

Also performed a 'apt-get remove --purge' as well.  

I am running 6.06 LTS - Dapper

uname -a 
Linux rfd 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Suggestions? 

Thanks!

-wx_nut

---

### Post by taurus on 2006-10-23
Have you tried "gksudo" instead of "gksu"?

---

### Post by wx_nut on 2006-10-23
Hi taurus:

Yes, I have. 
wx_nut@rfd:/etc$ sudo apt-get install gksudo
sudo: unable to lookup rfd via gethostbyname()
Reading package lists... Done
Building dependency tree... Done
Package gksudo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksudo has no installation candidate

Thanks, 

-wx_nut

---

### Post by invalid on 2006-10-23
gksudo is available 'out of the box'. What happens if you```
gksudo synaptic
```instead of using gksu?

---

### Post by wx_nut on 2006-10-23
Seems to pop right up. 

So then how do I solve the issue with clicking on stuff from gnome, without having to go to command line? 

Thanks, 

-wx_nut

---

### Post by taurus on 2006-10-23
Just clicking on stuff and if it requires you to be root, it will ask you for a password!!!  Otherwise, use gksudo, not gksu...

---

### Post by wx_nut on 2006-10-23
taurus:

The issue is, it's not asking for a password, nor is the program starting.  

Thanks, 

-wx_nut

---

### Post by wx_nut on 2006-10-23
Here is some additional information: 

wx_nut@rfd:/home$ gksu users-admin
sudo: unable to lookup rfd via gethostbyname()

(users-admin:10552): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Is this helpful at all? 

thanks, 

-wx_nut

---

### Post by wx_nut on 2006-10-24
Ok, I discovered the issue, or at least a fix. 

From what I can tell, sudo and gksu and gksudo all require a valid DNS entry.  It doesn't seem to matter where this entry is - it will look at both the /etc/hosts file and also in DNS - whatever those servers may be. 

So, what I did, was I added an entry in my /etc/hosts file to be 

rfd 127.0.0.1 

And this fixed the issue.  

I have a feeling it got removed when I added in Mike's Ad blocking hosts file - most likely I fat fingered it, like I tend to do as of late.  Now, does this pose any other risks to the system?  Potentially, but I haven't had time to investigate it further.

---

### Post by CatKiller on 2006-10-24
You're supposed to have an alias of your machine name to 127.0.0.1 in your /etc/hosts that matches your /etc/hostname, so it shouldn't pose any additional security risk. Glad you got it sorted.

---

### Post by slavik on 2006-11-14
I have the same problem ...

my /etc/hosts:
```

127.0.0.1 localhost slavik
127.0.1.1 slavik-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

my /etc/hostname:
```

slavik

```

EDIT:
In my case, this is the error when doing 'gksu users-admin' (same for gksudo)
```

(users-admin:11841): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by CatKiller on 2006-11-14
That error message is a known low-priority bug that doesn't mean anything.

If you are **actually** having problems using sudo, you could comment out the 127.0.1.1 line.

---

### Post by slavik on 2006-11-14
> **CatKiller said:**
> That error message is a known low-priority bug that doesn't mean anything.

If you are **actually** having problems using sudo, you could comment out the 127.0.1.1 line.
nope, doesn't work ...

I don't think that it should be a low priority bug since getting updates (security updates) cannot be considered low priority.

---

