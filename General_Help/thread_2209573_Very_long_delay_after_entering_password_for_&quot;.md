---
title: "Very long delay after entering password for &quot;sudo&quot;"
date: 2014-03-06
forum: General Help
---

### Post by vanadium on 2014-03-06
I am using Ubuntu 13.10. Since a few days, I have an issue where it takes up to 30 seconds before a sudo command actually is executed. For example, when I issue the command ```
sudo echo "here I am"
``` I immediately am requested my password. Then, nothing happens for about 30 seconds, before the output of the command appears. With the command "top" no activity can be seen during these 30 seconds.

The problem extends to other ways of authentication. Logging in to a text console (Ctrl+Alt+F1 through F6) exhibits a similar problem. After providing login and password, the prompt only appears after a long time. When a password is asked graphically, for example when installing a programme from software center, the password is asked. Then, the entry field of the password dialog disappears, but the dialog remains for a long time before the actual programme runs or action is performed.

I tried disabling dnsmasq as outlined [here ](http://www.dedoimedo.com/computers/ubuntu-dns-resolution.html) (removing symbolic link /etc/resolv.conf and replacing it by an empty text file instead). This resolved the sudo issue, but broke my internet: no webpages would be found. This is how I suspect it must be a DNS issue. My /etc/hosts file correctly states my local hostname
```
~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	vanadium

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Obviously, what went wrong here, and how could it be resolved? Are others experiencing the same problem?

---

### Post by TheFu on 2014-03-06
Have you touched any other files in /etc?  nsswitch.conf, host.conf any like that?  Check the timestamp on those files.
BTW, please put the original resolv.conf back - it is important. 

I'm thinking the order of host name resolution has been altered requiring very long attempts before the timeout is hit.
Any chance you touched anything in /etc/pam.d/ too?

---

