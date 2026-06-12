---
title: "Program Keeps Trying to Install Itself...  How Do I Stop It??"
date: 2007-03-20
forum: General Help
---

### Post by SendDerek on 2007-03-20
**[RESOLVED!]**

Hello All.

I have a problem with TuxShop.  I downloaded the .deb file and *tried* to install it but I could never get past the database setup.  Anyways, I've figured out that I don't need this program any longer so I just want it to stop trying to install.

Every time I install another program, either through synaptic or apt-get, it always pops up and tries to walk me through the configuration.  This has become a problem when trying to install apps through Automatix2 because it exits with an error and gives up in trying to install the apps that I want.

What steps can I take to get rid of this entirely?

Thanks for any help.

---

### Post by SendDerek on 2007-03-21
I found some more information...

I got this error while trying to install updates on my PC:
> 
E: tuxshoppro: subprocess post-installation script returned error exit status 127.


---

### Post by SendDerek on 2007-03-23
Where would I begin to look for a soultion to this little problem of mine?

Here's the log after trying to install lame for example:
```

<username>@vaio:~$ sudo apt-get install lame
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.88.4-1ubuntu2.1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu2.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
Setting up tuxshoppro (1.9) ...
cpio: /usr/share/applnk/Office/TuxShop/TuxShop.desktop not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/Status.desktop not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/.directory not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/dbSetup.desktop not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/Configuration/Preferences.desktop not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/Configuration/.directory not created: newer or same age version exists
cpio: /usr/share/applnk/Office/TuxShop/Configuration/dbInstall.desktop not created: newer or same age version exists
0 blocks
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/var/lib/dpkg/info/tuxshoppro.postinst: 12: /opt/tuxsoft/bin/Status: not found
dpkg: error processing tuxshoppro (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 tuxshoppro
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SendDerek on 2007-03-25
Is there a command I can issue to clear out what is trying to install?

---

### Post by SendDerek on 2007-03-27
I'm still searching for a solution...

---

### Post by mattwho on 2007-03-27
I had a similar problem with vmware. I had to uninstall vmware to fix it.

---

### Post by SendDerek on 2007-03-31
Thanks for your reply.

I cannot uninstall them using apt-get remove.  Is there another way to remove them or take them off of the "things to install list" (if there ever was one)?

---

### Post by Ramses de Norre on 2007-03-31
**sudo dpkg --purge -r tuxshoppro**

and if that doesn't work try this: **sudo dpkg --purge --force-remove-reinstreq -r tuxshoppro**

---

### Post by SendDerek on 2007-03-31
Thank you so much!!  That was the exact answer I was needing!  No more annoying pop-ups for me!

Thanks again!

---

### Post by Ramses de Norre on 2007-03-31
Nice 8)
May I ask which of the commands worked? Because I wasn't sure myself.

---

### Post by SendDerek on 2007-04-01
Well, yeah!  Sorry I didn't mention it before.

I used:

> 
sudo dpkg --purge tuxshoppro


I tried to use the -r extention but it conflicted with the --purge one.

I didn't need to use the other one you mentioned.

Thanks again for your help!

---

