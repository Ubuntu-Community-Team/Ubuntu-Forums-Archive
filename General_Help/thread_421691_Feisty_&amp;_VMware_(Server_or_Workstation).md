---
title: "Feisty &amp; VMware (Server or Workstation)"
date: 2007-04-24
forum: General Help
---

### Post by woifi on 2007-04-24
Hi!

Since I upgraded to Feisty, I have problems installing VMware Server (1.0.2) or Workstation (Beta6) -- the do only run with root permissions because the installer gives, I think, wrong permissions:

Here is an output of the vmware binarys in /usr/bin/
```
8,0K -r-x------ 1 root root 4,5K 2007-04-24 21:14 /usr/bin/vmware*
8,0K -r-x------ 1 root root 4,5K 2007-04-24 21:14 /usr/bin/vmware-acetool*
328K -r-x------ 1 root root 322K 2007-04-24 21:14 /usr/bin/vmware-config.pl*
288K -rw-r--r-- 1 root root 283K 2007-04-24 21:09 /usr/bin/vmware-config.pl.old.0
660K -r-x------ 1 root root 654K 2007-04-24 21:14 /usr/bin/vmware-loop*
 32K -r-x------ 1 root root  29K 2007-04-24 21:14 /usr/bin/vmware-mount.pl*
 12K -r-sr-xr-x 1 root root  11K 2007-04-24 21:14 /usr/bin/vmware-ping*
8,0K -r-x------ 1 root root 4,5K 2007-04-24 21:14 /usr/bin/vmware-tray*
148K -r-x------ 1 root root 141K 2007-04-24 21:14 /usr/bin/vmware-uninstall.pl*
148K -r-xr-xr-x 1 root root 141K 2007-04-24 21:16 /usr/bin/vmware-uninstall-vix.pl*
692K -r-x------ 1 root root 688K 2007-04-24 21:14 /usr/bin/vmware-vdiskmanager*
```

Also the files in /usr/lib/vmware have 500 or 400!

Anyone else with the same problems or a solution? ;)

bye

woifi


ps: just the vmware-server-console installs with right permissons (so I can start it with a normal user account).

---

### Post by sefs on 2007-04-24
1.0.2 does not install under feisty unless you use some patch which is in itself broken since the patch breaks wireless bridging.  So if you use wireless your guest os will not be able to access the internet. 

However with Workstation 6.0 beta... how did you install it?

1) copy the tar to your home directory 
2) unzip it
3) change to the vmware-distrb folder and 
4) sudo <intallfilename>.pl

?

That should just install it right away with correct permissions.

of course if vmware server was installed previously you might want to run the uninstall scrpit first and then install the workstation beta.

---

### Post by rbmorse on 2007-04-24
> **sefs said:**
> 
of course if vmware server was installed previously you might want to run the uninstall scrpit first and then install the workstation beta.

This is a necessary step,

---

### Post by woifi on 2007-04-25
hi!

> **sefs said:**
> 1.0.2 does not install under feisty unless you use some patch which is in itself broken since the patch breaks wireless bridging.  So if you use wireless your guest os will not be able to access the internet. 

However with Workstation 6.0 beta... how did you install it?

1) copy the tar to your home directory 
2) unzip it
3) change to the vmware-distrb folder and 
4) sudo <intallfilename>.pl

?

That should just install it right away with correct permissions.

of course if vmware server was installed previously you might want to run the uninstall scrpit first and then install the workstation beta.

Thank you for your reply!

I installed VMware Workstation that way you described and used the any-to-any patch for the server installation previously (I don't need wireless bridging). 

I also have a Debian Sarge Server with VMware Server here -> no problem to install.
```
-r-xr-xr-x  1 root root   4570 2007-01-09 13:31 /usr/bin/vmware
-r-xr-xr-x  1 root root  73092 2007-01-09 13:31 /usr/bin/vmware-authtrusted
-r-xr-xr-x  1 root root  23333 2007-01-09 13:31 /usr/bin/vmware-cmd
-r-xr-xr-x  1 root root 289216 2007-01-09 13:31 /usr/bin/vmware-config.pl
-r-xr-xr-x  1 root root 490464 2007-01-09 13:31 /usr/bin/vmware-loop
-r-xr-xr-x  1 root root  25488 2007-01-09 13:31 /usr/bin/vmware-mount.pl
-r-sr-xr-x  1 root root  10852 2007-01-09 13:31 /usr/bin/vmware-ping
-r-xr-xr-x  1 root root  99602 2007-01-09 13:31 /usr/bin/vmware-uninstall.pl
-r-xr-xr-x  1 root root 715960 2007-01-09 13:31 /usr/bin/vmware-vdiskmanager
```

It would be no problem to chmod the binaries, but it would be very tricky to do this under /usr/lib/vmware.

Any other hints?

bye

woifi

---

### Post by woifi on 2007-04-26
Well, wasn't so tricky to chmod:
```
sudo chmod go+rx /usr/bin/vmware*
sudo chmod -R go+rx /usr/lib/vmware/
sudo chmod -R go+r /usr/share/doc/vmware
```
VMware Workstation 6.0beta runs fine now :).

---

