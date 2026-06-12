---
title: "synaptic software index broken"
date: 2006-08-23
forum: General Help
---

### Post by cptjaben on 2006-08-23
today when I tried to run synaptic, i got the message "software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. when I ran sudo apt-get install -f" in the terminal i got this message: 

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-core compiz-gnome compiz-plugins
The following NEW packages will be installed:
  compiz-core compiz-plugins
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/681kB of archives.
After unpacking 1534kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102231 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.37-0ubuntu4_i386.deb) ...
Unpacking compiz-plugins (from .../compiz-plugins_0.2-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-gnome
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace compiz-gnome 0.0.13-0quinn34 (using .../compiz-gnome_0.0.13.37-0ubuntu4_i386.deb) ...
Unapplying schemas...
Done.
Unpacking replacement compiz-gnome ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-plugins_0.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know what this means or how to fix it?

Thanks,
cptjaben

---

### Post by Saibot on 2006-08-24
This happened to me today also.  Open Synaptic and in the Edit menu go to Fix Broken Packages.  That fixed my problem,  I think I had to run the update manager again too to get everything resolved.

---

### Post by cptjaben on 2006-08-24
Thanks for the help Saibot, it fixed mine as well.

---

### Post by lgmdaniel on 2006-09-06
I have this same problem but when I try to fix it I get the following error.

First this when I apply...

> samba (version 3.0.22-1ubuntu3) will be upgraded to version 3.0.22-1ubuntu3.1
Then the following error

> E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102

---

### Post by lgmdaniel on 2006-09-19
Anyone able to help me with this? I don't want to have to go though re-installing.

---

### Post by unwoken on 2006-09-25
> **lgmdaniel said:**
> Anyone able to help me with this? I don't want to have to go though re-installing.

lgmdaniel.  Don't know if you are still having this problem, but i had the same problem as you.

i can't explain the mechanics (i'm sure someone else can), but i found the solution here, (quoted from somewhere else):  [http://ubuntuforums.org/showthread.php?t=247000&page=2&highlight=samba+error+102](http://ubuntuforums.org/showthread.php?t=247000&page=2&highlight=samba+error+102)  

it says this: 

> 
Originally Posted by Sebata_Afrika
- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba
- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.


the above fixed my system.  maybe it's worth a try if you (or anyone else) is still having this problem.

u.

---

### Post by lgmdaniel on 2006-09-26
I still do have the problem.. though that didn't help as K09samba doesn't exsist. Thanks anyway...

---

### Post by lgmdaniel on 2006-09-27
looks like I've fixed it...
rm'd this in /etc/r2.d and rc3.d
lrwxrwxrwx 1 root root  6 2006-06-15 18:49 S91samba -> /samba

---

