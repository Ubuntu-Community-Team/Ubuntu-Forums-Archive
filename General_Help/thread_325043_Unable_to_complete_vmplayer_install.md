---
title: "Unable to complete vmplayer install"
date: 2006-12-24
forum: General Help
---

### Post by jgb2185 on 2006-12-24
I am unable to complete the vmware player installation under Dapper, as described in [the Ubuntu online documentation]("https://help.ubuntu.com/community/VMware/Player?action=show"). All goes well until the installer attempts to build the vmmon module:

```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

mknod: `/dev/vmmon': File exists
Unable to create the character device /dev/vmmon with major number 10 and minor
number 165.

Execution aborted.

```

I am uncertain how to proceed. Can anyone advise me regarding a fix for this problem?

Many thanks...

JGB

---

### Post by taurus on 2006-12-24
What was the exact command you ran to get that error message?

---

### Post by jgb2185 on 2006-12-24
Here's the sequence I ran, as root:
```
apt-get install build-essential
uname -r
apt-get install linux-headers-2.6.15-26-386
apt-get install gcc-3.4
apt-get install g++-3.4
cd /home/jgb/downloads
wget http://download3.vmware.com/software/vmplayer/VMware-player-1.0.3-34682.tar.gz
tar xvzf VMware-player-1.0.3-34682.tar.gz
cd vmware-player-distrib
export CC=/usr/bin/gcc-3.4
./vmware-install.pl
```

JGB

---

### Post by taurus on 2006-12-24
```
sudo ./vmware-install.pl
```

---

### Post by jgb2185 on 2006-12-25
I am not certain what your point is, taurus. I ran [FONT="Courier New"]**./vmware-install.pl**[/FONT] as root, as I stated above.

Some googling on this error seems to indicate that it may be related to the use of udev to manage /dev. While I see some possible solutions that can be applied after installation, I do not see any way to resolve the issue in mid-installation.

JGB

---

