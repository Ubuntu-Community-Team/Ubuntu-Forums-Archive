---
title: "Creating certificate for openvpn"
date: 2018-04-29
forum: General Help
---

### Post by sniper8752 on 2018-04-29
I am trying to create my certificate for openvpn.  I am running ubuntu server 16.  I was getting an error saying ```
 No /etc/openvpn/easy-rsa/openssl.cnf file could be found  Further invocations will fail

```
So I went into the vars file and updated this line: ```
export KEY_CONFIG=`$EASY_RSA/*openssl-1.0.0.cnf* $EASY_RSA`
```
I then had permissions issues:
```
-rw-r--r-- 1 root root  8313 Apr 28 21:51 openssl-1.0.0.cnf
```
```
source vars
bash: /etc/openvpn/easy-rsa/openssl-1.0.0.cnf: Permission denied
```
So I used the permissions of the whichopensslcnf file:
```
-rwxr-xr-x 1 root root  8313 Apr 28 21:51 openssl-1.0.0.cnf
```
When I run source vars now: ```
root@server:/etc/openvpn/easy-rsa# source vars/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 5: HOME: command not found
/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 6: RANDFILE: command not found
/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 7: openssl_conf: command not found
/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 12: oid_section: command not found
/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 13: engines: command not found
/etc/openvpn/easy-rsa/openssl-1.0.0.cnf: line 32: default_ca: command not found
dir: cannot access '=': No such file or directory
dir: cannot access '::KEY_DIR': No such file or directory
.....

```

How do I get this to work?  Is this the right way to fix this?

---

### Post by sniper8752 on 2018-05-04
*bump*

---

### Post by altjx on 2018-05-20
> **sniper8752 said:**
> *bump*

Would be nice if we could figure this out. Same issue here. 5 minute OpenVPN install has now turned into a night of 2+ hours of troubleshooting.

Try this:

sudo ln -s openssl-1.0.0.cnf openssl.cnf

---

