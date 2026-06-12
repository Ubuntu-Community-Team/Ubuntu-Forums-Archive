---
title: "Cant Update"
date: 2006-11-02
forum: General Help
---

### Post by chedabob on 2006-11-02
The little icon on in the notification area says "error:brokencount>0", and when i run it, it tells me to run synaptic or try "sudo apt-get -f install". I tried it, and it didnt fix it. It just tells me it needs to install some stuff, and that its not authenticated, then it just fails.

Heres the output of terminal:

```

matt@matt-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libevent-rpc-perl anyevent-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libanyevent-perl
The following NEW packages will be installed
  libanyevent-perl
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
1 not fully installed or removed.
Need to get 0B/17.4kB of archives.
After unpacking 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libanyevent-perl
Install these packages without verification [y/N]? y
(Reading database ... 128498 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_1.02-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@matt-desktop:~$ 


```

any ideas?

EDIT:

I tried "sudo apt-get autoremove" and "sudo apt-get autoremove -f". With the -f i get:

```
matt@matt-desktop:~$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libevent-rpc-perl anyevent-perl
The following extra packages will be installed:
  libanyevent-perl
The following packages will be REMOVED
  anyevent-perl libevent-rpc-perl
The following NEW packages will be installed
  libanyevent-perl
0 upgraded, 1 newly installed, 2 to remove and 30 not upgraded.
1 not fully installed or removed.
Need to get 0B/17.4kB of archives.
After unpacking 295kB disk space will be freed.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libanyevent-perl
Install these packages without verification [y/N]? y
(Reading database ... 128498 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_1.02-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chedabob on 2006-11-03
Any ideas guys?

---

### Post by klahjn on 2006-12-01
> **chedabob said:**
> Any ideas guys?

this is how i fixed it.

```
 dpkg -r anyevent-perl
(Reading database ... 229697 files and directories currently installed.)
Removing anyevent-perl ...
# apt-get install -f 
```

---

### Post by La muerte del DIos on 2007-06-05
Worked perfect for me. I wish to know how to do this stuff, the day my Internet connection dies i won't be able to do ****. Thank you very much.;)

---

