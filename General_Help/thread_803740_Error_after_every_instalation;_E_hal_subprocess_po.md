---
title: "Error after every instalation; E: hal: subprocess post-installation script returned e"
date: 2008-05-22
forum: General Help
---

### Post by JimmyI on 2008-05-22
Hi,

I've done a clean install of Hardy and now everytime I install something I get the following error 

E: hal: subprocess post-installation script returned error exit status 1

The application installs but its just a bit anoying having this pop up all the time.

I get an option for an expanded breakdown and this is as follows;Preconfiguring packages ...
(Reading database ... 96605 files and directories currently installed.)
Preparing to replace libssl0.9.8 0.9.8g-4ubuntu3 (using .../libssl0.9.8_0.9.8g-4ubuntu3.1_i386.deb) ...
Unpacking replacement libssl0.9.8 ...
Preparing to replace openssh-client 1:4.7p1-8ubuntu1 (using .../openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace openssl 0.9.8g-4ubuntu3 (using .../openssl_0.9.8g-4ubuntu3.1_i386.deb) ...
Unpacking replacement openssl ...
Preparing to replace ssh-askpass-gnome 1:4.7p1-8ubuntu1 (using .../ssh-askpass-gnome_1%3a4.7p1-8ubuntu1.2_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Selecting previously deselected package openssl-blacklist.
Unpacking openssl-blacklist (from .../openssl-blacklist_0.1-0ubuntu0.8.04.2_all.deb) ...
Preparing to replace ssl-cert 1.0.14-0ubuntu2 (using .../ssl-cert_1.0.14-0ubuntu2.1_all.deb) ...
Unpacking replacement ssl-cert ...
Setting up hal (0.5.11~rc2-1ubuntu8) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libssl0.9.8 (0.9.8g-4ubuntu3.1) ...

Setting up openssh-client (1:4.7p1-8ubuntu1.2) ...

Setting up openssl (0.9.8g-4ubuntu3.1) ...

Setting up ssh-askpass-gnome (1:4.7p1-8ubuntu1.2) ...

Setting up openssl-blacklist (0.1-0ubuntu0.8.04.2) ...
Setting up ssl-cert (1.0.14-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hal (0.5.11~rc2-1ubuntu8) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1

Any help would be appreciated
James

---

### Post by JimmyI on 2008-05-24
okay, I really could do with some help on this? I thought everything was installing okay but there not. I currently can't get any kind of unrar program working which is severely limiting my ubuntu use..

---

### Post by JimmyI on 2008-05-25
Hi,

I've reinstalled Hardy from scratch and the problem wasn't there at first, but after I updated the system the error came back?

Has any one else had this?

Jim

---

