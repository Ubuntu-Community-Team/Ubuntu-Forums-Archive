---
title: "how do i get or downlaod VMWARE on FEISTY FAWN 7.04"
date: 2007-08-31
forum: General Help
---

### Post by gundumfx on 2007-08-31
how do i get or downlaod VMWARE on FEISTY FAWN 7.04??

i tryed a lot but i could not get it so i am asking you know so please help thanks

---

### Post by gletob on 2007-08-31
For server:
Get Key: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
Get Vmware: sudo apt-get install vmware-server

For Player: sudo apt-get install vmware-player

---

### Post by gtdaqua on 2007-09-01
This is a doc that i prepared for my own reference. See if this helps. I have done this on both Intel 64 and AMD64.

Build Environment
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.

**
aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd
**

for server
**
sudo aptitude install libxtst6 libxt6 libxrender1
**

for 64-bit
**
sudo apt-get install ia32-libs libc6-i386
**

**Downloading VMware Server**
Vmware Server can be downloaded from:
 [http://www.vmware.com/download/server/]("http://www.vmware.com/download/server/")
After accepting the EULA grab the vmware server .tgz file (around 102MB).
[B]Note: As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file.
[/B]
Patch information can be found here: 

[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

The patch can be downloaded here: [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

**Installing VMware Server**

Untar the VMware Server package:
**
tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
**

Change into the install directory:
**
cd vmware-server-distrib
**

Run the installer:
**
sudo vmware-install.pl
**

Choose defaults to questions until it asks:

"Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]"

Enter NO and quit the install. To install the patch cd back to your start directory:
cd ..

Untar the patch:
**
tar xvzf /Path/To/vmware-any-any-update109.tar.gz 
**

Enter the directory: 
**
cd vmware-any-any-update109
**

Run the patch script:
**
sudo ./runme.pl
**

It should prompt you to run vmware-config.pl, Choose YES at this time. If it doesn't you can always run the config script manually:
**
sudo vmware-config.pl
**

Again you can hit enter to choose the defaults to all the questions, though you will probably want to manually choose which networking features you want. To access the server run
**
vmware
**
for the VMware Server Console.


**To get the remote Mangegment Interface:**

Download Mangement Inteface from VMWare Download Site

**
tar zxvf VMware-mui-<xxx>.tar.gz
sudo ./vmware-install.pl
**

If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.
**
sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl
**

If you want to administer VMware from the server itself with a minimal set of GUI

KDE Environment
**
sudo apt-get install kdebase kdm x-window-system-core
**

---

### Post by 101binary on 2007-09-01
Hi

Excelent walktrough.  I still get a "error while loading shared libraries: libxext.so.6 (no such file/lib).  I am running server 7.03 with no gui.  Allready used the - aptitude install lib* commands.

If there is any assistance that you could offer, i would really appreciate it!  

Thanks

---

### Post by gtdaqua on 2007-09-01
when exactly are you getting that message? when loading the compiler? there is afix for it - i had the problem too and fixed by installing some gcc compiler - not sure of the name.


u could get a better walkthrough here:

[http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server")

---

### Post by gundumfx on 2007-09-01
> **gletob said:**
> For server:
Get Key: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
Get Vmware: sudo apt-get install vmware-server

For Player: sudo apt-get install vmware-player
hey do you ave to pay for this ??

---

### Post by gundumfx on 2007-09-01
> **gtdaqua said:**
> This is a doc that i prepared for my own reference. See if this helps. I have done this on both Intel 64 and AMD64.

Build Environment
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.

**
aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd
**

for server
**
sudo aptitude install libxtst6 libxt6 libxrender1
**

for 64-bit
**
sudo apt-get install ia32-libs libc6-i386
**

**Downloading VMware Server**
Vmware Server can be downloaded from:
 [http://www.vmware.com/download/server/]("http://www.vmware.com/download/server/")
After accepting the EULA grab the vmware server .tgz file (around 102MB).
[B]Note: As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file.
[/B]
Patch information can be found here: 

[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

The patch can be downloaded here: [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

**Installing VMware Server**

Untar the VMware Server package:
**
tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
**

Change into the install directory:
**
cd vmware-server-distrib
**

Run the installer:
**
sudo vmware-install.pl
**

Choose defaults to questions until it asks:

"Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]"

Enter NO and quit the install. To install the patch cd back to your start directory:
cd ..

Untar the patch:
**
tar xvzf /Path/To/vmware-any-any-update109.tar.gz 
**

Enter the directory: 
**
cd vmware-any-any-update109
**

Run the patch script:
**
sudo ./runme.pl
**

It should prompt you to run vmware-config.pl, Choose YES at this time. If it doesn't you can always run the config script manually:
**
sudo vmware-config.pl
**

Again you can hit enter to choose the defaults to all the questions, though you will probably want to manually choose which networking features you want. To access the server run
**
vmware
**
for the VMware Server Console.


**To get the remote Mangegment Interface:**

Download Mangement Inteface from VMWare Download Site

**
tar zxvf VMware-mui-<xxx>.tar.gz
sudo ./vmware-install.pl
**

If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.
**
sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl
**

If you want to administer VMware from the server itself with a minimal set of GUI

KDE Environment
**
sudo apt-get install kdebase kdm x-window-system-core
**
well thanks for the walk through but i use intel Pentium 4 not amd or intel 64

---

