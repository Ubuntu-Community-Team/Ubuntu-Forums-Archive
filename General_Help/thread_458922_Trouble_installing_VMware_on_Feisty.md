---
title: "Trouble installing VMware on Feisty"
date: 2007-05-30
forum: General Help
---

### Post by OsakaWilson on 2007-05-30
I'm on a computer with 64bit Feisty and I want to install VMware. I'm trying to follow the directions at [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)
but I only get as far as putting sudo apt-get install vmware-server vmware-tools-kernel-modules into the console. It gives me the following message. 

 &#9474; A previous installation of a VMware product has been detected.            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you installed it from the VMware website, please remove it by running  &#9474;  
 &#9474; vmware-uninstall.pl before proceeding.                                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If it was installed through Ubuntu, you must purge (completely remove)    &#9474;  
 &#9474; the old package.  

After I hit OK from this error message, I get the following:

Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe libssl0.9.7 0.9.7k-3 [758kB]
Fetched 758kB in 0s (1735kB/s)
Preconfiguring packages ...
Selecting previously deselected package vmware-server-kernel-modules.
(Reading database ... 141901 files and directories currently installed.)
Unpacking vmware-server-kernel-modules (from .../vmware-server-kernel-modules_2.6.20.16.28.1_amd64.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7k-3_amd64.deb) ...
Unpacking vmware-server (from .../vmware-server_1.0.3-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.3-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried to install VMware before in various ways but couldn't get it to work, so there could be some remnants of VMware on my system. I tried uninstalling, as they suggest in the second line of the message, but when I try that, I get:

bash: vmware-uninstall.pl: command not found

I went to synaptic and uninstalled anything related to VMware, but that didn't work either. 

Any ideas. The head of my IT department is visiting tomorrow and he is interested in Ubuntu. It would be perfect if I could show him Windows running on Ubuntu. 

OsakaWilson

---

### Post by vmikalinis on 2007-05-30
I just removed mine using the full path,

If you unzipped it to /tmp:

/tmp/vmware-server-distrib/bin/vmware-uninstall.pl


I'm stopped at the install :

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

---

### Post by vmikalinis on 2007-05-30
ok so now I fixed some of it by editing my /etc/pam.d/vmware-authd and removing the full paths such as 

/usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix2.so shadow nullok

is now : pam_unix2.so shadow nullok

My working file:

#%PAM-1.0
auth       sufficient       pam_unix2.so shadow nullok
auth       required         pam_unix_auth.so shadow nullok
account    sufficient       pam_unix2.so
account    required         pam_unix_acct.so
 


Once I fixed that and ran vmware I am left with the error of :

/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

---

### Post by OsakaWilson on 2007-05-31
I don't know the path that was  used. I've tried installing it from Synaptic, from the website, from Automatix and they all have failed. I have no idea how many broken attempts at installing are in my system. 

I did all the clean-up tricks from this thread:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Still it said there is a previously installed version and won't let me procede. 

Anyone know how to purge VMware from my system?

---

### Post by wthanna on 2007-05-31
see the 2nd post of this thread.... it's what worked for me

[http://ubuntuforums.org/showthread.php?t=450466](http://ubuntuforums.org/showthread.php?t=450466)

---

### Post by OsakaWilson on 2007-06-01
wthanna,

That did it for me too. Thank you. On to installing Windows XP...

---

