---
title: "Deleted my /etc/hosts file by mistake"
date: 2012-11-27
forum: General Help
---

### Post by duranl on 2012-11-27
Following some poorly written advice on a forum, I deleted the contents of my /etc/hosts file and saved it like that.  How can I get the information back?

---

### Post by DukeOfMixture on 2012-11-27
Were the contents of your hosts file the default contents or did you have customized data in it?

By default,** as far as I know** the hosts file contains only the following:

```
127.0.0.1  localhost 
 
::1  localhost #[IPv6]
```

---

### Post by StinkySQL on 2012-11-27
I have a generic 12.04 64-bit system (Dell 1501) with the following hosts file contents:
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Hope that helps
SS
Hope that helps

---

### Post by sdowney717 on 2012-11-27
here is mine
> 127.0.0.1	localhost
127.0.1.1	scott-P5QC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by ZippyUbu on 2012-11-27
Hi,

Here is mine, fresh install in Virtualbox:

```

127.0.0.1    localhost
127.0.1.1    ubu-VirtualBox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by rnerwein on 2012-11-28
> **ZippyUbu said:**
> Hi,

Here is mine, fresh install in Virtualbox:

```

127.0.0.1    localhost
127.0.1.1    ubu-VirtualBox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
just create a new one with the contes you got posted ( replace the hostname to yours)
and chown root:root /etc/hosts
        chmod 644 /etc/hosts

---

### Post by Habitual on 2012-11-28
> **duranl said:**
> ...How can I get the information back?

```
cp /etc/hosts /etc/hosts.bak
```THEN, and only then can you 
```
rm /etc/hosts
``` :)

[http://www.bournetoraiseshell.com/article.php/20120716202359537](http://www.bournetoraiseshell.com/article.php/20120716202359537)

---

