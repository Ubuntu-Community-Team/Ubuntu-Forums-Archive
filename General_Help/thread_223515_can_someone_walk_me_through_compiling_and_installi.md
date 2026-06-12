---
title: "can someone walk me through compiling and installing of a wireless driver?"
date: 2006-07-26
forum: General Help
---

### Post by bionnaki on 2006-07-26
info:

dapper
linksys wmp54g pci network adapter
rt2500 chipset + rt2500 drivers that ship with ubuntu

I am connected to the internet wirelessly using this card. I was able to use wpa using the following /etc/network/interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ra0 inet static
address 192.168.1.xx
netmask 255.255.255.0
gateway 192.168.x.x
pre-up iwconfig ra0 essid xxxx
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=x
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="xxxxx"
pre-up iwpriv ra0 set TxRate=0

auto ra0


Internet connection comes up on reboot and stays online, but it drops randomly - every 15 seconds or every 15 mins. signal strength will drop to 0% for a few seconds and then go back up again. This has made using the internet very frustrating.

following the advice of this thread: [http://www.ubuntuforums.org/showthread.php?p=1299462#post1299462](http://www.ubuntuforums.org/showthread.php?p=1299462#post1299462)

I'd like to install the beta driver for my card to see if it improves my connectivity. I do not know how to compile and install the driver. I see in the readme file that comes with the driver, I should do this:

> For 2.4 or 2.6 series kernel:
a. $tar -xvzf rt2500-x.x.x.tar.gz
    go to "./rt2500-x.x.x/Module" directory.

b. $make                # compile driver source code

c. $make install	# installs kernel module driver 


ok, havent tried this yet, but then what? is that all I have to do (besides reboot)?

If someone could walk me through this, I would greatly appreciate it. thanks!

---

### Post by bionnaki on 2006-07-26
when I try to make, I get this:

> frank@ubuntu:~$ cd /home/frank/rt2500-1.1.0-b4/Module
frank@ubuntu:~/rt2500-1.1.0-b4/Module$ make
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
rt2500.ko failed to build!
make: *** [module] Error 1


any ideas?

---

### Post by bionnaki on 2006-07-31
bump

---

### Post by bionnaki on 2006-07-31
ok, so after reading a few things, I decided to:

> sudo apt-get install linux-headers-`uname -r`

afterwards, I was able to "make":

> frank@ubuntu:~/rt2500-1.1.0-b4/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_main.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/mlme.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/connect.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/sync.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/assoc.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/auth.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/auth_rsp.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_data.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_init.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/sanity.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_wep.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/wpa.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/md5.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_tkip.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/rtmp_info.o
  CC [M]  /home/frank/rt2500-1.1.0-b4/Module/eeprom.o
  LD [M]  /home/frank/rt2500-1.1.0-b4/Module/rt2500.o
  Building modules, stage 2.
  MODPOST
  CC      /home/frank/rt2500-1.1.0-b4/Module/rt2500.mod.o
  LD [M]  /home/frank/rt2500-1.1.0-b4/Module/rt2500.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'


but when I "make install" I get these errors:

> frank@ubuntu:~/rt2500-1.1.0-b4/Module$ make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/frank/rt2500-1.1.0-b4/Modu le  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /home/frank/rt2500-1.1.0-b4/Module/rt2500.ko
mkdir: cannot create directory `/lib/modules/2.6.15-26-386/extra': Permission de nied
cp: cannot create regular file `/lib/modules/2.6.15-26-386/extra': Permission de nied
make[2]: *** [/home/frank/rt2500-1.1.0-b4/Module/rt2500.ko] Error 1
make[1]: *** [modules_install] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [modules_install] Error 2


so, then I tried to do that with sudo:

> 
frank@ubuntu:~/rt2500-1.1.0-b4/Module$ sudo make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/frank/rt2500-1.1.0-b4/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /home/frank/rt2500-1.1.0-b4/Module/rt2500.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
/sbin/depmod -a
grep: /etc/modprobe.conf: No such file or directory
append 'alias ra0 rt2500' to /etc/modprobe.conf


hmmm...any ideas?

---

