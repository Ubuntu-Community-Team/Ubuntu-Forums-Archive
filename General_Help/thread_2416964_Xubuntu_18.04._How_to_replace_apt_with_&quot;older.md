---
title: "Xubuntu 18.04. How to replace apt with &quot;older&quot; version"
date: 2019-04-18
forum: General Help
---

### Post by twgray on 2019-04-18
When I had Xubuntu 16.04 installed I installed Bodhi Linux as an alternative desktop.  This installed higher numbered version of apt.  This caused several problems  with the 18.04 upgrade. Now, I can't get rid of the bodhi version in favor of the recommended version which has a lower version number. If I try to force the "lower" version I get errors about attempting to overwrite some html file also used by the Bodhi apt package.  

Am I correct in believing that I can't remove the Bodhi version of apt completely and then install the xubuntu version?

---

### Post by Rubi1200 on 2019-04-18
Hi,

I'm not clear on the situation. Bodhi is a separate distro? Do you mean you installed the DE from Bodhi in Xubuntu? And I thought Bodhi uses a web-based software center?

---

### Post by twgray on 2019-04-19
I installed Bodhi Enlightenment Desktop as an alternative desktop...just as you might install Gnome, KDE, etc.  When I installed it, it replaced my apt package with with apt version 2.2.12-bodhi2.  After purging all Bodhi and/or enlightenment packages I am still left with this version of apt and it is preventing me from installing apt-utils, which depends on apt 1.6.  When I try to force installation with:

sudo apt -f install apt_1.6.6ubuntu0.1_amd64.deb 

I get the following error:

dpkg: error processing archive /var/cache/apt/archives/apt_1.6.6ubuntu0.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/apt/methods/https', which is also in package apt-transport-https 2.2.12~bodhi2

Anyone with a clue about how to "fix" this "catch-22"?

---

### Post by twgray on 2019-04-19
Turns out apt-transport-https is no longer needed as it is included in apt starting with version 5.

Also, the way to overcome the issue if it was still needed is with the following:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/apt_1.6.6ubuntu0.1_amd64.deb

---

