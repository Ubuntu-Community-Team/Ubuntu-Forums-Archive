---
title: "linux-headers-2.6.20"
date: 2007-02-14
forum: General Help
---

### Post by gnarula on 2007-02-14
Hi!

I am using Dapper (6.06) and using the latest kernel 2.6.20. I want to use the fglrx driver so thought of installing it but i need the linux headers.. am looking for:
linux-headers-2.6.20

if there is some repository which has it then please tell me..

Gaurav

---

### Post by dantum on 2007-02-14
Hi,

I compiled my 2.6.20 kernel using this guide. When you create the package for kernel-image you also create kernel header package which you install too.

I haven't managed to install fglrx yet with 2.6.20 , working on it.

Dan

I just managed to install fglrx 8.33 with stock 2.6.20 kernel. I used the patch from this thread

[http://ubuntuforums.org/showthread.php?t=353772](http://ubuntuforums.org/showthread.php?t=353772)

patch link -> [http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch)

You need to run the ati-driver-installer-8.33.6-x86.x86_64.run and choose Uknown X system setup. Once installed finished you need to go to 

cd /lib/modules/fglrx/build_mod 
patch -p6 < /<location of patch file>/8.33/fglrx-2.6.20.patch
./make.sh
cd ..
./make_install

Like it is mentioned in other thread. The trick is to go not generate ubuntu specific packages. 

just my $.02c

---

### Post by gnarula on 2007-02-14
thnx! will try it!

---

