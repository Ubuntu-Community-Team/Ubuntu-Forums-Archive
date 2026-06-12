---
title: "Need help installing SIPX – error when apt-getting"
date: 2007-07-11
forum: General Help
---

### Post by obeattie on 2007-07-11
Hey Everyone,

Just so you know, I'm completely new to Ubuntu. I'm normally a Mac OS X-ian (please don't lynch me for that!)

I've installed Ubuntu Server and am pretty comfortable using the Command Line to do everything. But I've come across a problem when I run

```
sudo apt-get install -t stable sipxpbx
```

I'm following [this]("http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu#Setup_Ubuntu_apt_Package_Management") guide, but I just get this error when I run the ``apt-get install``:

```
oliver@sip-server:~$ sudo apt-get install -t stable sipxpbx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  sipxpbx: Depends: libsipxcommserver1 but it is not going to be installed
           Depends: sipxregistry (>= 3.4) but it is not going to be installed
           Depends: sipxproxy (>= 3.4) but it is not going to be installed
           Depends: sipxpublisher (>= 3.4) but it is not going to be installed
           Depends: sipxvxml (>= 3.4) but it is not going to be installed
E: Broken packages
```

I'm know it's probably me just being a complete bumpkin, and so would really appreciate any help you could offer me!

Thanks a lot!
Oliver

---

### Post by figgles on 2007-07-21
What version of ubuntu (dapper, fiesty, etc) are you running?

---

### Post by eshax on 2008-04-25
sipx only run in server version ?

---

### Post by eshax on 2008-04-26
You can download the requested file from the pool/main/i/icu/ subdirectory at:

    * [security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1.6.06.1_i386.deb")

---

