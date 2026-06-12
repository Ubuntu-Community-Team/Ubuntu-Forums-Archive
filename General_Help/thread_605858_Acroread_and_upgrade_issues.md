---
title: "Acroread and upgrade issues"
date: 2007-11-07
forum: General Help
---

### Post by Avenolpey on 2007-11-07
I was trying to upgrade from Acrobat 7.x to 8.1 and seem to have hosed my system. My upgrade manager is giving me this message.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Also when I try to install Acroread I get these errors. Can someone help.

root@ubuntu:/home/spencer# apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libatk1.0-0 (>= 1.13.2) but 1.11.4-0ubuntu1 is to be installed
            Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
            Depends: libglib2.0-0 (>= 2.14.0) but 2.10.3-0ubuntu1 is to be installed
            Depends: libgtk2.0-0 (>= 2.12.0) but 2.8.20-0ubuntu1.1 is to be installed
            Depends: libpango1.0-0 (>= 1.18.2) but 1.12.3-0ubuntu3 is to be installed
            Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is to be installed


Thanks,

Spencer

---

### Post by taurus on 2007-11-07
Not a good idea to log in as root!  If you need to be root to install something, use sudo.  So, log in with your account and run

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Avenolpey on 2007-11-07
Thanks Taurus,

When I run wget this is the response.

spencer@ubuntu:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
gpg: no valid OpenPGP data found.

---

### Post by taurus on 2007-11-07
Looks like the site is hosed!  Therefore, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the line [http://packages.medibuntu.org](http://packages.medibuntu.org) to comment it out.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Okay, here's the link, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by Avenolpey on 2007-11-07
Thanks again Taurus, that worked. However it reloaded Acrobat 7.09. Do you know if 8.1 is now supported?

---

