---
title: "Problem installing VHCS control panel - need help urgently please"
date: 2007-12-07
forum: General Help
---

### Post by latheesan on 2007-12-07
Hello,

I recently bought a new dedicated server and the operating system running on it is Debian 4.0 Etch 64-bit eddition.

It doesnt come with a control panel, so i decided to install the VHCS since it looks like it can do exactly what other commercial cp software can do such as cPanel, DirectAdmin etc...

So, i came across this guide and decided to install it: [http://vhcs.puuhis.net/wiki/index.php/Getting_started](http://vhcs.puuhis.net/wiki/index.php/Getting_started)

When i typed the command: apt-get install vhcs* i get the following error:

Debian-40-etch-64-LAMP:~# apt-get install vhcs*
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vhcs_dump.sql
Debian-40-etch-64-LAMP:~#

I followed the guide correctly and setup my source list to have this respority:

deb [http://apt.scunc.it/](http://apt.scunc.it/) etch main 

and then did the apt-get update, but it's still no help. It keeps saying it cant find that vhcs_dump.sql file... Are there any other respority that anyone know of? or a possible solution to this problem? Please advice.

---

