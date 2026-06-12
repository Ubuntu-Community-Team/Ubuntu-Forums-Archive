---
title: "Adobe Air installation issues"
date: 2008-05-05
forum: General Help
---

### Post by wesy2kn1 on 2008-05-05
So I googled how to install adobe air for linux on 8.04 and followed the instructions found here [http://www.sizlopedia.com/2008/04/06/how-to-install-adobe-air-on-ubuntu/]("http://www.sizlopedia.com/2008/04/06/how-to-install-adobe-air-on-ubuntu/") and I'm getting an error from air setup that says An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.

Tried going root, but this didn't work. Any recommendations?

---

### Post by mrsudo on 2008-07-17
i was having the same problem.  you must close firefox before installing
hope this helps :)

---

### Post by SteVader on 2008-09-02
I too was having the same trouble in Kubuntu. Thanks for the tip about closing Firefox mrsudo!

---

### Post by lotvx on 2009-07-27
it happens to me too, but i dont have any browser open

here is a solution for fedora

[http://rootblock.wordpress.com/2009/06/24/fedora-11-adobe-air-installation-not-allowed-by-administrator/](http://rootblock.wordpress.com/2009/06/24/fedora-11-adobe-air-installation-not-allowed-by-administrator/)




An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.

This problem occurs due to missing packages.

How to fix? Install the following:

yum -y install xterm gtk2-devel gnome-keyring libxml2-devel libxslt rpm-devel nss

Then run the .bin file again.

[xterm might be needed for a pop up terminal requesting a root password when installing air or air apps]

---

### Post by lotvx on 2009-07-28
/Solved

what i did was to look for the folder /opt/Adobe Air that already existed. so i changed its name, and now is working. you need administrative privileges to rename or acces the folder, so i did sudo nautilus and then renamed


Resuelto

Lo que pasaba era que ya existia la carpeta /opt/Adobe air
asi que le cambie el nombre y listo, instalo

---

### Post by rjpilla on 2009-09-07
SOLVED!! Delete the adobe-cert package from synaptic. If not there check the etc/opt folder and delete the Adobe folder. Air will install after this. Make sure you did complete removal of broken package also from your previous tries.  Enjoy

---

