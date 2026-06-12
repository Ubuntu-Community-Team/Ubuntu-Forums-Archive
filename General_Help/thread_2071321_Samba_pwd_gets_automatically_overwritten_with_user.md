---
title: "Samba pwd gets automatically overwritten with user pwd"
date: 2012-10-15
forum: General Help
---

### Post by reach on 2012-10-15
Hi there!
I'm using 12.04 server
Think the title explaines my problem already, however, here's the details:
I want my main user to have a different system password than the samba password. I set it using "sudo smbpasswd user"
It works but after a while it's back to the system password.
I haven't thoroughly researched if this happens only after reboot, but I'm pretty sure it happens even without that, just after a few hours.

I googled a little and came across the hint to de-install "libpam-smbpass"
I tried so, but it doesn't do it due to a dependency with linux-headers-....
Maybe I don't even have it installed? I don't know how to find this out, I'm quite a noob. 

Any hints?
Thx!

---

### Post by Tralce on 2012-10-15
Maybe this is a noobish solution, but when I had that issue on my desktop I installed system-config-samba (which requires python-glade2 and a GUI) but it does allow you to set passwords for samba users other than their own account passwords.

---

### Post by reach on 2012-10-16
> **Tralce said:**
> Maybe this is a noobish solution, but when I had that issue on my desktop I installed system-config-samba (which requires python-glade2 and a GUI) but it does allow you to set passwords for samba users other than their own account passwords.

Thanks, but I'm afraid that doesn't really help me with me bash-only server OS. Or does it?
I'm using webmin and it also has a similar option, but it is DISabled, so it shouldn't happen anyway

Any other thoughts?

---

### Post by PowerBarry43 on 2012-10-16
you can run from a command line the command
```

smbpasswd -a yourusername
```

which will allow you to set or reset samba passwords, webmin should allow you to do this as well but I've often found that just using this command is much more reliable.

Hope this helps!

Barry

---

### Post by Morbius1 on 2012-10-16
The very first thing I do with a new install is remove libpam-smbpass if it sneaks into the base install. Never once did I receive a message about linux headers although I never installed the server version of Ubuntu either.

Just to make sure it is in fact installed:
```
dpkg -s libpam-smbpass | grep Status
```If I look at my own system and run the following command to see what it's dependencies are:
```
apt-cache depends libpam-smbpass
```Or this one to find out if libpam-smbpass is a dependancy of something else:
```
apt-cache rdepends libpam-smbpass
```I get no reference to linux headers.

Sorry, not much help here but if it's not libpam-smbpass which would be the usual suspect given your description of the problem I'm not sure what is syncing the 2 passwords.

---

