---
title: "problem getting some packages"
date: 2005-08-27
forum: General Help
---

### Post by fractalvibes on 2005-08-27
I got the postgres database software and then the pgamin3  GUI tool.  Having problems connecting to the database via pgadmin3 (works fine from command line).

Someone on the pgadmin list suggested that I needed also to get the pidentd package.   I did so via synaptic, but I don't think the install was successfull.

dpkg -l pidentd  reveals:
root@PhiLinux:/home/fractalvibes # dpkg -l pidentd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  pidentd        3.0.16-7       TCP/IP IDENT protocol server with DES support

Likewise when I tried getting/installing webmin via synaptic : 
 
root@PhiLinux:/home/fractalvibes # dpkg -l webmin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  webmin         1.180-2        web-based administration toolkit

I have uninstallled/removed via synaptic and redid both via apt-get with the same results.

Any idea what is happening here to cause the package install to not be successful?

thanks,

fv

---

### Post by arnieboy on 2005-08-27
[QUOTE=fractalvibes]I got the postgres database software and then the pgamin3  GUI tool.  Having problems connecting to the database via pgadmin3 (works fine from command line).

Someone on the pgadmin list suggested that I needed also to get the pidentd package.   I did so via synaptic, but I don't think the install was successfull.

dpkg -l pidentd  reveals:
root@PhiLinux:/home/fractalvibes # dpkg -l pidentd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  pidentd        3.0.16-7       TCP/IP IDENT protocol server with DES support

Likewise when I tried getting/installing webmin via synaptic : 
 
root@PhiLinux:/home/fractalvibes # dpkg -l webmin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  webmin         1.180-2        web-based administration toolkit

I have uninstallled/removed via synaptic and redid both via apt-get with the same results.

Any idea what is happening here to cause the package install to not be successful?

thanks,

fv[/QUOTE]

firstly make sure your repositories are set up correctly. refer to [http://ubuntuguide.org#repositories](http://ubuntuguide.org#repositories)
then do a ```
sudo apt-get update
```
Then open up synaptic and look for the section called "broken" that will have the broken packages. if there arent any then remove webmin and pidentd and install tem with apt-get once again
```
sudo apt-get install pidentd webmin
```

---

### Post by fractalvibes on 2005-08-28
Ok - thanks.  I did all the above steps,  Synaptic indicated no broken packages.
Completely ininstalled both packages via synaptic.  Did apt-get upgrade, apt-get updates, did apt-get install pidentd  webmin - both appeared to download and installed without error.  dpkg   -l still reporting half-installed.  So I must have some incompatability problem? 

thanks,

fv

 
root@PhiLinux:/home/fractalvibes # dpkg -l pidentd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  pidentd        3.0.16-7       TCP/IP IDENT protocol server with DES suppor
root@PhiLinux:/home/fractalvibes # dpkg -l webmin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  webmin         1.180-2        web-based administration toolkit

---

