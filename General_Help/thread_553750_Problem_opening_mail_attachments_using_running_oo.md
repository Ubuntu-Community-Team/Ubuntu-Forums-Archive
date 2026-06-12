---
title: "Problem opening mail attachments using running oo"
date: 2007-09-18
forum: General Help
---

### Post by holger2 on 2007-09-18
Hi,

I recently switched Linux distribution from Debian Sarge to Ubuntu Feisty and since that I've the following problem opening mail attachments using openoffice (mostly doc-attachments): my system is unable to use a running instance of openoffice to open the attachment. The attachment is loaded into openoffice _only_ if there is no openoffice already running. Otherwise I get the oo error message "/tmp/[file_name] does not exist".

Any suggestions how to fix this problem? The mail program I use is mutt, and the relevant line in my .mutt.mailcap is:

application/msword; ooffice %s


Holger

---

### Post by holger2 on 2007-09-20
> **holger2 said:**
> Hi,

I recently switched Linux distribution from Debian Sarge to Ubuntu Feisty and since that I've the following problem opening mail attachments using openoffice (mostly doc-attachments): my system is unable to use a running instance of openoffice to open the attachment. The attachment is loaded into openoffice _only_ if there is no openoffice already running. Otherwise I get the oo error message "/tmp/[file_name] does not exist".



Just to answer myself.... My problem seems to be the effect of a known Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/70981](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/70981)

In the link the bug is suspected to be KDE-related. I use Gnome, so perhaps that is the wrong way to go when searching for root of the problem..

---

