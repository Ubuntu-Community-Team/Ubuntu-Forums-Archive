---
title: "package dependency issue, is it a bug?"
date: 2013-07-05
forum: General Help
---

### Post by jannetyang on 2013-07-05
Hi:

when I tried to install php5 on a ubuntu 12.04 server, it said that it depends on apache2-mpm-prefork or apache2-mpm-itk. But when I tried to install these 2 apache2 packages, it said that they are confliced with another apache2 package, do you have any idea how I can move on and install php5? thank you very much!
------------------------------------------------------
root@GU-Innova:~/php5# sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gettext : Depends: libcroco3 (>= 0.6.2) but it is not installable
           Depends: libgomp1 (>= 4.2.1) but it is not installable
           Depends: libunistring0 but it is not installable
           Depends: libgettextpo0 (= 0.18.1.1-5ubuntu3) but it is not installable
 [U]libapache2-mod-php5 : Depends: apache2-mpm-prefork (> 2.0.52) but it is not installable or
                                apache2-mpm-itk but it is not installable
   [/U]                    Recommends: php5-cli but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

------------------------------------------------------------
root@GU-Innova:~/apache2# dpkg -i apache2-mpm-prefork_2.2.22-1ubuntu1.2_amd64.deb
dpkg: regarding apache2-mpm-prefork_2.2.22-1ubuntu1.2_amd64.deb containing apache2-mpm-prefork:
[U] apache2-mpm-prefork conflicts with apache2-mpm
  apache2-mpm-event provides apache2-mpm and is present and installed.
[/U]dpkg: error processing apache2-mpm-prefork_2.2.22-1ubuntu1.2_amd64.deb (--install):
 conflicting packages - not installing apache2-mpm-prefork
Errors were encountered while processing:
 apache2-mpm-prefork_2.2.22-1ubuntu1.2_amd64.deb
------------------------------------------------------------

root@GU-Innova:~/apache2# dpkg -i apache2-mpm-itk_2.2.20-1ubuntu1_amd64.deb
dpkg: regarding apache2-mpm-itk_2.2.20-1ubuntu1_amd64.deb containing apache2-mpm-itk:
[U] apache2-mpm-itk conflicts with apache2-mpm
  apache2-mpm-event provides apache2-mpm and is present and installed.[/U]
dpkg: error processing apache2-mpm-itk_2.2.20-1ubuntu1_amd64.deb (--install):
 conflicting packages - not installing apache2-mpm-itk
Errors were encountered while processing:
 apache2-mpm-itk_2.2.20-1ubuntu1_amd64.deb
root@GU-Innova:~/apache2#

---

### Post by jannetyang on 2013-07-05
should I uninstall apache2 first? or just uninstall _apache2-mpm-event_?

---

### Post by CaptainMark on 2013-07-05
Your error message is telling you what to do, you currently have broken packages on your system```
sudo apt-get install -f
```Then re-try your original apt-get command and report back with the results

---

