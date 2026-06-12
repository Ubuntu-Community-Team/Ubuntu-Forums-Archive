---
title: "[SOLVED] Deluge-torrent Installation Dependant Libraries Missing"
date: 2008-02-14
forum: General Help
---

### Post by galeg on 2008-02-14
Have just tried to apt-get install deluge-torrent, but have received the errors below.

> grant@ubuntu:~$ sudo apt-get install deluge-torrent

Reading package lists... Done

Building dependency tree       

Reading state information... Done

deluge-torrent is already the newest version.

You might want to run `apt-get -f install' to correct these:

The following packages have unmet dependencies:

  deluge-torrent: Depends: libboost-date-time1.34.1 but it is not going to be installed

                  Depends: libboost-filesystem1.34.1 but it is not going to be installed

                  Depends: libboost-thread1.34.1 but it is not going to be installed

                  Depends: python-pyopenssl but it is not going to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 

It appears that I can install the python-pyopenssl from apt-get, but can somebody please advise how I install the libboost dependents.
Thanks

---

### Post by aeiah on 2008-02-14
they are available at packages.ubutu.com, although there's probably a reason why they arent installing via apt-get. did you run 'apt-get -f install' as proposed? have you got the right repos enabled in your sources.list? what happens when you run sudo apt-get install libboost-thread1.34.1?

---

### Post by galeg on 2008-02-14
Thanks aeiah

Have checked available packages and agree that all appear to be listed, but I find it interesting in Software Sources that there was no reference to Gutsy 7.1 (which is the version I am running), but nearly everything referred to Feisty 7.04.

I did run the -f install option with no change, and also attempted to install each fill individually, also with no change.

You are probably correct that I do not have the correct repos enable in the sources.list, so can you give me an idea of, either what entry I should activate, or what entry I should insert.

---

### Post by galeg on 2008-02-15
Manually installed libs that were reported as missing.

---

