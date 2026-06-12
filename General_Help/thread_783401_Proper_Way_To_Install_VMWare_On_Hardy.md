---
title: "Proper Way To Install VMWare On Hardy?"
date: 2008-05-05
forum: General Help
---

### Post by SupaRice on 2008-05-05
I'm installing Hardy on my HP laptop, and it's going to be my main OS on the box.  I'm still going to dual boot with Win XP, but I want to finally make the leap into using Linux as my main workstation.  However to do this I'm going to have to get VMWare going in Hardy as there are some company apps that only work in Winblows.

SO.... What is the proper way to isntall VMWare server in Hardy?

---

### Post by cenwesi on 2008-05-06
here is how...
============================
In terminal.

  $ apt-get install build-essential linux-headers-`uname -r`
  $ apt-get install xinetd

next download vmware server and expand it out somewhere

  $ tar -xvzf VMware-server-1.0.5-80187.tar.gz

then do the install

  $ cd vmware-server-distrib
  $ ./vmware-install.pl

next, next, yada yada. Eventually it will start compiling and fail.

grab the any to any patch 116 from

  $ wget [http://uruz.org/files/vmware-any-any-update-116.tgz](http://uruz.org/files/vmware-any-any-update-116.tgz)
  $ tar -xvzf vmware-any-any-update116.tgz
  $ cd vmware-any-any-update116
  $ ./runme.pl

Finally you can configure vmware server (note this usually will be run automatically at the end of the any-any patch, no need to run it twice)

  $ vmware-config.pl

answer all the questions and it should compile fine.

once installed I received an error trying to launch vmware so I cheated and copied the libraries over, which seems to have resolved that issue.

  $ ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
  $ ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

---

### Post by registering on 2008-05-06
Thank you so much!!!

---

