---
title: "Synaptic and Medibuntu Repositories"
date: 2007-10-20
forum: General Help
---

### Post by Elrian on 2007-10-20
Hello i repost this message here because i posted in the wrong section before!

Here is my problem:

On my Gutsy install i added the Medibuntu repositories to my sourcelist according to the tutorial on their new website. (Yes i updated the repositories using both the terminal and synaptic).

But when i try to search for apps like Google Earth or Skype they don't show up in the Synaptic (Graphic Interface)...

I can still install them through the terminal via apt-get but since im not very command friendly can anyone help me fix this problem?

If apt-get can find the repos in the console why don't they show in the synaptic graphical interface?

Thank a lot for your answers!

---

### Post by bigbrovar on 2007-10-20
mehn am having the same problem with synaptics returning nothing for my search result..even when the packages are avaliable in my repo

---

### Post by Elrian on 2007-10-20
> **bigbrovar said:**
> mehn am having the same problem with synaptics returning nothing for my search result..even when the packages are avaliable in my repo

So i am not the only one having this problem!

Anyone can help us fix it?

---

### Post by por100pre1 on 2007-10-20
Weird, this could be some kind of bug.

To search via CLI:

```
aptitude search *package-name*
```

Please post the result of this:

```
cat /etc/apt/sources.list
```

Check that this line is present and uncommented (without #):

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

EDIT: I suspect the Medibuntu repository is mentioned in /etc/apt/sources.list.d/medibuntu.list and this file is NOT well recognized. :-k

---

### Post by Elrian on 2007-10-21
Here is my source list:

# Réalisation automatique par le générateur de fichiers sources.list
# Le 20/10/2007 à 15:45 (Europe/Paris) sur le site [http://www.sourceslist.org](http://www.sourceslist.org)
#
# En cas de soucis, vous pouvez contacter le webmaster par email [email]webmaster@sourceslist.org[/email]
#
# Pays : France
# Release : Gutsy
# Architecture : i386 (Processeurs 32-bits)
#

#########################################
### Depot Ubuntu

#section: Ubuntu Gutsy Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports multiverse

#section: Ubuntu Gutsy Security
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

#section: Ubuntu Gutsy Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

#section: Ubuntu Gutsy 7.10
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

#section: Ubuntu Gutsy Proposed
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed multiverse

#########################################
### Depot Canonical

#section: Ubuntu Gutsy 7.10
deb [http://archive.canonical.com/](http://archive.canonical.com/) gutsy partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) gutsy partner

#########################################
### Depot Medibuntu
## KEY GPG: wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

#section: Medibuntu testing packages for Ubuntu Gutsy 7.10
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy-staging free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy-staging free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy-staging non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy-staging non-free

#section: Medibuntu packages for Ubuntu Gutsy 7.10
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy non-free

---

### Post by Shazaam on 2007-10-21
FYI two of my dapper(official) and ALL of my medibuntu repos have been failing for the last couple of days so it might be a server issue.

---

### Post by Elrian on 2007-10-21
Yes might be just that it works now!

---

