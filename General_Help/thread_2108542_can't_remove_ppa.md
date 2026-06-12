---
title: "can't remove ppa"
date: 2013-01-24
forum: General Help
---

### Post by dwlamb on 2013-01-24
I mistakenly installed a ppa that has installed a pre-release of LibreOffice.  I want to roll back to a more stable release but can not get rid of the ppa.

```
sudo add-apt-repository --remove ppa:LP-PPA-libreoffice-libreoffice-prereleases/quantal
Cannot access PPA (https://launchpad.net/api/1.0/~LP-PPA-libreoffice-libreoffice-prereleases/+archive/quantal) to get PPA information, please check your internet connection.

```I am on a high speed permanent connection.  There is no problem with my internet connection.  Is there another method to remove this ppa?

---

### Post by ibjsb4 on 2013-01-24
Check out ppa-purge.  Its in the software center.

[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

---

### Post by gifford on 2013-01-24
You can use software center-software resources. Or, if installed, synaptic and go to repositories.

---

### Post by SeijiSensei on 2013-01-24
If you just want to remove the PPA from your sources, you can delete (as root with sudo) the relevant file in /etc/apt/sources.list.d/.  That's where most PPAs now place the reference to the source.  You'll still have the key stored somewhere, but the PPA itself will no longer be used as a source.

Make sure to run "sudo apt-get update" after you remove the file.

---

### Post by dwlamb on 2013-01-25
thanks alll!  you're advice helped and I am now a happy camper.:p

---

