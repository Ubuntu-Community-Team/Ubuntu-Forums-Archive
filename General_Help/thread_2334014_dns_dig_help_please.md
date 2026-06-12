---
title: "dns dig help please"
date: 2016-08-15
forum: General Help
---

### Post by Joe67 on 2016-08-15
i need to do a dns dig +trace on my ubuntu 12.04 lts vps to check my domains i recently changes to another host.... i dont think dig +trace is working, or installed, can anyone help please?

---

### Post by Habitual on 2016-08-15
> **Joe67 said:**
> i need to do a dns dig +trace on my ubuntu 12.04 lts vps to check my domains i recently changes to another host.... i dont think dig +trace is working, or installed, can anyone help please?

in terminal:
```
dig domain.tld @8.8.8.8 +short 
```
The 8.8.8.8 here is Google's DNS server.

You can check your nameservers using
```
dig domain.tld @ns1_ip +short
dig domain.tld @ns2_ip +short
```
where ns[12]_ip are the public IPs of your designated nameservers.

```
+short is for just the IP
```

They should match.

---

### Post by Joe67 on 2016-08-17
getting the message:


-bash: dig: command not found

---

### Post by SeijiSensei on 2016-08-17
Check that the package **dnsutils** is installed.  

If the **bind9-host** package is installed, you can use:
```
$ host -t ns example.com
```
which should return something like 
```

example.com name server a.iana-servers.net.
example.com name server b.iana-servers.net.

```

By default, without "-t something" host returns the IP address in the A record.  You can check for other types of records like "host -t mx example.com" or "host -t txt example.com".

Every Ubuntu version I've used has the bind9-host package installed by default.

---

### Post by Joe67 on 2016-08-17
Thanks

Heres what ive tried since..

```
dpkg -s dnsutilsPackage `dnsutils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.



```
i then tried ```
sudo apt-get install dnsutilsReading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bind9 bind9-host bind9utils libbind9-80 libdns81 libisc83 libisccc80
  libisccfg82 liblwres80
Suggested packages:
  bind9-doc resolvconf ufw rblcheck
The following NEW packages will be installed:
  dnsutils
The following packages will be upgraded:
  bind9 bind9-host bind9utils libbind9-80 libdns81 libisc83 libisccc80
  libisccfg82 liblwres80
9 upgraded, 1 newly installed, 0 to remove and 329 not upgraded.
Need to get 1643 kB of archives.
After this operation, 393 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com/ubuntu/ precise-updates/main bind9 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main bind9 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main bind9-host amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libisc83 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libdns81 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libisccc80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libisccfg82 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main liblwres80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main bind9utils amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libbind9-80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main dnsutils amd64 1:9.8.1.dfsg.P1-4ubuntu0.11
  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9utils_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.11_amd64.deb  404  Not Found [IP: 91.189.88.161 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

i then try
```
apt-get updateE: Type 'EOFcat' is not known on line 10 in source list /etc/apt/sources.list
E: The list of sources could not be read.
```

---

### Post by Joe67 on 2016-08-18
is this a problem with the ubuntu mirror?

---

### Post by SeijiSensei on 2016-08-18
Have you tried again since posting the above?  Yes, it looks like the mirror is unavailable.  Try another one.  Here's the list:
```

$ host security.ubuntu.com
security.ubuntu.com has address 91.189.91.23
security.ubuntu.com has address 91.189.88.149
security.ubuntu.com has address 91.189.88.161
security.ubuntu.com has address 91.189.91.26
security.ubuntu.com has address 91.189.88.152
security.ubuntu.com has address 91.189.88.162

```
If you still cannot connect to 91.189.88.161, edit (as root with sudo) /etc/hosts and add an entry for one of the other mirrors, e.g.,
```

91.189.91.23     security.ubuntu.com

```
Then run "sudo apt-get update".  Any better?

---

### Post by Joe67 on 2016-08-18
no luck yet, latest was 91.189.88.162 80]

bare with me mate :D

heres what i have in hosts

```
fe00::0        ip6-localnet
ff00::0        ip6-mcastprefix
ff02::1        ip6-allnodes
ff02::2        ip6-allrouters


127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
217.***.**.** mydomain.com  mydomainname
::1        localhost ip6-localhost ip6-loopback
```

should i add it to the top?

---

### Post by SeijiSensei on 2016-08-18
Top. Bottom. Anywhere.  The order of entries in fstab is irrelevant.

---

### Post by Joe67 on 2016-08-18
roger that, i get the error

```
~# sudo apt-get updateE: Type 'EOFcat' is not known on line 10 in source list /etc/apt/sources.list
E: The list of sources could not be read.



```

---

### Post by SeijiSensei on 2016-08-18
Something mucked up your sources.list file.  Did you try editing it manually?  It should only contain comments starting with hash marks ("#") and lines starting with "deb" or with "deb-src".  Here's mine, for example.  I use the mirror at MIT since I live in Greater Boston:
```

# deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.1)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirrors.mit.edu/ubuntu/ trusty main restricted
deb-src http://mirrors.mit.edu/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.mit.edu/ubuntu/ trusty-updates main restricted
deb-src http://mirrors.mit.edu/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.mit.edu/ubuntu/ trusty universe
deb-src http://mirrors.mit.edu/ubuntu/ trusty universe
deb http://mirrors.mit.edu/ubuntu/ trusty-updates universe
deb-src http://mirrors.mit.edu/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.mit.edu/ubuntu/ trusty multiverse
deb-src http://mirrors.mit.edu/ubuntu/ trusty multiverse
deb http://mirrors.mit.edu/ubuntu/ trusty-updates multiverse
deb-src http://mirrors.mit.edu/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.mit.edu/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.mit.edu/ubuntu/ trusty-backports main restricted universe multiverse

deb http://mirrors.mit.edu/ubuntu/ trusty-security main restricted
deb-src http://mirrors.mit.edu/ubuntu/ trusty-security main restricted
deb http://mirrors.mit.edu/ubuntu/ trusty-security universe
deb-src http://mirrors.mit.edu/ubuntu/ trusty-security universe
deb http://mirrors.mit.edu/ubuntu/ trusty-security multiverse
deb-src http://mirrors.mit.edu/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

This is for 14.04 (Trusty). Yours should have "precise" where mine has "trusty."

---

### Post by Joe67 on 2016-08-18
here it is:


i dont remember having to edit it 
```
deb http://archive.ubuntu.com/ubuntu precise main restricted universedeb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe
deb http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu precise partner


deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
EOFcat >> /etc/apt/sources.list <<-EOF
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib



```

---

### Post by Joe67 on 2016-08-18
alright dig seems to be working now

ive moved my domains over to the same host i use for vps, my domains were all pointing to the ip using www. and @ A records.. Ive set them up but for some reason the domains arnt working..

i now need to figure out how to use dig, to check the domains

---

### Post by Joe67 on 2016-08-18
problem fixed, thanks for the help

---

