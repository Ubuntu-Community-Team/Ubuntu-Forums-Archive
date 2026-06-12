---
title: "Update Manager - 403 Forbidden Error"
date: 2007-11-16
forum: General Help
---

### Post by manatee7 on 2007-11-16
Hey, 
I'm having problems downloading libsmbclient / samba / samba-common and smbclient using the update manager, it is giving me this:
> 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden



My sources list is original Gutsy. :confused:

---

### Post by Perfect Storm on 2007-11-16
Seems there's problem with that package I can't get too. Just hold on until it's fixed.

---

### Post by arcole on 2007-11-16
same prob

ubuntu server 7.10

```
The following packages will be upgraded:
  file-roller libgnomeui-0 libgnomeui-common libpango1.0-0 libpango1.0-common samba samba-common
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6677kB/8176kB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com gutsy-security/main samba 3.0.26a-1ubuntu2.1
  403 Forbidden
Err http://security.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by taurus on 2007-11-16
[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

---

### Post by OnoA on 2007-11-16
Same with the desktop...

I guess it's just a little rights problem.

The Release File will scan the package no matter if the webserver user has the right to read it or not. So apt says there's a new package, but it won't be able to download it.

So just relax and stay tuned... as soon as somebody notices the mistake it will be a couple of seconds to fix.

:guitar:

---

### Post by Perfect Storm on 2007-11-16
> **taurus said:**
> [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

Ah! Then I have to wait to compile VLC ;)

---

### Post by camurgo on 2007-11-16
I'm getting the very same error here :confused:

---

### Post by camurgo on 2007-11-16
> **taurus said:**
> [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

Thx

---

### Post by GrammatonCleric on 2007-11-16
ditto.

---

### Post by n122103 on 2007-11-16
Hi, just want to confirm the issue remains as of 17:06 EST (22:06 GMT).

Thanks :)

EDIT:

After a bit of further research, I found that this has been stickied in the installation and upgrade forum.  More details on the issue can be found _[in this thread]("http://ubuntuforums.org/showthread.php?t=463944")_.

---

### Post by k-panic on 2007-11-16
yep... problem not solved yet...

---

### Post by n122103 on 2007-11-16
EDIT:

Moved info to first page

---

### Post by LuisC-SM on 2007-11-16
This thread tends to go longer if nothing happens in the next hours.

Same problem here after a fresh new install

---

### Post by kasperfish on 2007-11-16
indeed same problem....

---

### Post by foerdi on 2007-11-16
same problem with with samba.deb from security server

---

### Post by james_bandido on 2007-11-16
got the same error too ...

---

### Post by pixel_juice on 2007-11-16
I'm having the same problems getting:

libsmbclient
samba-common
smbclient

This effects all Ubuntu PCs I have.

---

### Post by Jroller90 on 2007-11-16
I am also having the problem :(

2:44 PM PST

---

### Post by wladston on 2007-11-16
confirming the issue is still happening on 22:12 GMT ...

guys - shouldn't ubuntu give a better error message on the gui ? I was called by my 10-year-old brother, that thought ubuntu "broke" ...

---

### Post by Sef on 2007-11-16
> guys - shouldn't ubuntu give a better error message on the gui ? I was called by my 10-year-old brother, that thought ubuntu "broke" ...


It said that Ubuntu failed to fetch the packages.   That is what happened.    As to why, you need a human to give a more detailed explanation.   In a way, your brother is right, part of the system is not working right, so that part of the system is broke.

---

### Post by Dyus36 on 2007-11-16
theres no way to bypass the broken links in the meantime?
im trying to upgrade a system from the beta cd to the full os but its being blocked by just 
these 4 packages, seems kind of pointless.

---

### Post by Happy_Man on 2007-11-16
> **Dyus36 said:**
> theres no way to bypass the broken links in the meantime?
im trying to upgrade a system from the beta cd to the full os but its being blocked by just 
these 4 packages, seems kind of pointless.
You could always uncheck those packages, and then update.

---

### Post by por100pre1 on 2007-11-16
> **Happy_Man said:**
> You could always uncheck those packages, and then update.

You can also use another server:

```
gksu software-properties-gtk
```

---

### Post by woodsby on 2007-11-16
Not being able to download a samba security update makes me nervous.

---

### Post by mlsquad on 2007-11-17
Same problem here.  I'm glad I found this thread.  I thought I was going crazy.

---

### Post by Perfect Storm on 2007-11-17
It's fixed now.

---

### Post by IanW on 2007-11-17
The locked Samba updates have now been released. Happy upgrades everyone.

---

### Post by in_flu_ence on 2007-11-17
Fixed with a apt upgrade

---

### Post by SyL on 2007-11-17
yep i confirm with with apt-get upgrade it does work

---

### Post by jeanh on 2007-11-17
Sam problem here using the update manager interface on the desktop.
Yet, we are Nov. 17th 2007...:(

Will try apt-get in the meantime.

Regards,
Jean

---

### Post by TalioGladius on 2007-11-17
about freaking time, I was about to kill that balloon telling me I had updates.

---

### Post by chrome101 on 2007-11-17
Its working... I Wonder what happened there?

---

### Post by arcole on 2007-11-17
:guitar: YAY all fixed!

---

### Post by heat84 on 2007-11-17
> **Artificial Intelligence said:**
> It's fixed now.

No it isn't.:(
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden



Maybe the permission change has to trickle to all the update servers and hasn't gotten to the one I connect to yet?
How can install Samba without doing the updates?

---

### Post by k-panic on 2007-11-17
Just try doing a 

```
sudo apt-get update; sudo apt-get upgrade
```

It should work. I was getting the same error after the problem was solved... and that did it.

---

### Post by heat84 on 2007-11-17
That worked thanks.:)

---

### Post by americanLoki on 2007-11-17
Update manager kept giving me a 403 forbidden error today but typing
```
sudo aptitude update && sudo aptitude upgrade
```
worked great and let me update with no problems.

---

