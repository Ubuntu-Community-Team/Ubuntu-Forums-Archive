---
title: "deinstallation Samba goes wrong"
date: 2005-04-02
forum: General Help
---

### Post by Webgnome on 2005-04-02
Hi all, 

a few days ago I tried to install Samba. But this didnt work for some reason. Now I'm trying to deinstall  it because the package manager says its installed but ofcourse i'm getting some errors. 

The problem with this samba is that it generating all kinds of errors when i try to upgrade or install stuff. 

Can somebody help me? 

here is the log of what i'm getting when trying to uninstall Samba

```

(reading database ... 66753 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script return error with exit status 102
dpkg: samba-comon: depency problems, but removing anyway as you request:
 samba depends on samba-comon ( = 3.0.7-lubuntu6.3).
Removing samba-common...

Failed to apply all changes! scroll in this buffer to see what went wrong

```

---

### Post by Webgnome on 2005-04-05
he people, i really dont know how to proceed in this manner. could someone please assist ?

---

### Post by segrewb on 2005-04-08
I found this here [APT HOWTO](http://www.debian.org/doc/manuals/apt-howto/index.en.html).  Maybe this will help.  

Look at 7.1 (Common errors) > 

If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands: 

     # apt-get -f install
     # dpkg --configure -a

Hope this helps.

---

