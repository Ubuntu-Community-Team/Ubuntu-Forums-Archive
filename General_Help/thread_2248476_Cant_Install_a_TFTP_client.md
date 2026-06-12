---
title: "Cant Install a TFTP client"
date: 2014-10-15
forum: General Help
---

### Post by Jat_Cheema on 2014-10-15
Hi,

I've downloaded the latest ubuntu last week and installed on a laptop.

However FTP is installed fine but there is no package for TFTP installed. I've tried the local [B][I]sudo apt-get install tftp or tftp-hpa but nothing is installed.


[/I][/B]I then used the Software center GUI to find  TFTP and nothing was shown. Then looking for TFTP on ubuntu website found lucid. However this fails to install due to libaries missing which I tried to install too.

Is there a TFTP client that is available and can be installed without these issues.

Thanks
Jat

---

### Post by HermanAB on 2014-10-15
Howdy,

The answer is here:
[http://www.aeronetworks.ca/2014/05/tftp-server-on-fedora-linux.html](http://www.aeronetworks.ca/2014/05/tftp-server-on-fedora-linux.html)

---

### Post by spjackson on 2014-10-15
> **Jat_Cheema said:**
> 
I've downloaded the latest ubuntu last week and installed on a laptop.

However FTP is installed fine but there is no package for TFTP installed. I've tried the local [B][I]sudo apt-get install tftp or tftp-hpa but nothing is installed.
[/I][/B]
Are you sure? This works for me on Trusty.
```
$ tftp
The program 'tftp' can be found in the following packages:
 * tftp-hpa
 * tftp
Try: sudo apt-get install <selected package>
$ sudo apt-get install tftp
[sudo] password for XXXXXXXX:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  tftp

<details deleted>
$ tftp
tftp> 

```
It also appears to be available for utopic. [http://packages.ubuntu.com/utopic/tftp](http://packages.ubuntu.com/utopic/tftp)

---

### Post by deadflowr on 2014-10-15
Open up the update manager, go to settings in the bottom left corner click on it,  and see that the universe repository is enabled.
(It'll be listed in the first window)

edit: I should note, as I forgot, after enabling(and even if enabling is not needed) run the "check" option in the update manager, and apply all updates.

---

