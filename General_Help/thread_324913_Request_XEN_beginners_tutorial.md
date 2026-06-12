---
title: "Request: XEN beginners tutorial"
date: 2006-12-24
forum: General Help
---

### Post by tomplast on 2006-12-24
Hi everyone. Please read my whole message before you start to give me a lot of links that I will most likely ignore (if you have failed to read what I have had to say).

I have tried on several occassions to get Xen working for me on my Ubuntu 6.10 installation. I have tried to follow the XenOnEdgy Wiki and several threads here and howtos all over the Web but none have given me success. 

I am quite experienced with Ubuntu and involved in projects around it so please believe me when I say that it haven't worked for me. From what I can read I'm far from the only one who have had problems with Xen, I think even someone called it "Black Voodoo Magic"  which seems understandable to me with the struggle that I have had with it.

The "best" result I have got is a rebooting computer (my system where Xen is installed!) which I don't appreciate that much.


I have tried other virtualization technologies as VmWare or Qemu but none of them have lived up to my expectations, which I happend to believe Xen could. I could as well wait for KVM but as it won't be included until kernel version 2.6.20 and Feisty Fawn isn't ready yet it's not an option for me. 


What I'm asking for is a simple step by step guide that covers how to install Xen and how to get it running under Ubuntu 6.10, and please do NOT point me to the XenOnEdgy wiki or something like that because I'm tired of have tried them over and over again several times withouth getting it working.


Thank you for your help

---

### Post by brottman on 2007-01-20
No idea how old this thread is as I found it in a search, but heres a good bump to bring it to the top again. Could someone smarter than I please educate us lowly types about all this stuff?

---

### Post by tomplast on 2007-01-22
> **brottman said:**
> No idea how old this thread is as I found it in a search, but heres a good bump to bring it to the top again. Could someone smarter than I please educate us lowly types about all this stuff?

Nice that someone joined me finally ;). Hopefully someone will pay attention to this thread soon :E

---

### Post by ggee on 2007-01-26
Hate to say it, but me too.  I have been trying to get Xen to run on Dapper or Edgy for the past few days.  My main problem has been that compiling Xen from source doesn't include the drivers for my SATA for some reason.  But Ubuntu does seem to recognize my sata.

So I found that there were Ubuntu pakages for Edgy.  I tried quite a few.  apt-get doesn't work for some reason of it points to reposisitories that don't have all the files.  So the following are the packages that have gotten me the closest.

[http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-source/xen-headers-2.6.19-1-generic-amd64_2.6.19-1_amd64.deb](http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-source/xen-headers-2.6.19-1-generic-amd64_2.6.19-1_amd64.deb)
[http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-source/xen-image-2.6.19-1-generic-amd64_2.6.19-1_amd64.deb](http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-source/xen-image-2.6.19-1-generic-amd64_2.6.19-1_amd64.deb)
[http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-hypervisor-3.0-amd64_3.0.3-0ubuntu1_amd64.deb](http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-hypervisor-3.0-amd64_3.0.3-0ubuntu1_amd64.deb)
[http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-ioemu-3.0_3.0.3-0ubuntu1_amd64.deb](http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-ioemu-3.0_3.0.3-0ubuntu1_amd64.deb)
[http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-utils-3.0_3.0.3-0ubuntu1_amd64.deb](http://gulus.usherbrooke.ca/pub/distro/ubuntu/pool/universe/x/xen-3.0/xen-utils-3.0_3.0.3-0ubuntu1_amd64.deb)

With the above packages, it actaully boots into dom0.  All other packages never fully boot.  Where I need help is compiling the following for my dom0 so I can get LAN working.

[http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2V/Linux_LAN.zip](http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2V/Linux_LAN.zip)

I'd really like to find the person that made these packages.

Binary: xen-headers-2.6.19-1-server, xen-headers-2.6.19-1, xen-image-2.6.19-1-server, xen-image-2.6.19-1-generic, xen-image-2.6.19-1-generic-amd64, xen-headers-2.6.19-1-generic-amd64, xen-headers-2.6.19-1-generic
Maintainer: Chuck Short <zulcss@ubuntu.com>

Not all these files are on the repositories and the headers package I downloaded contains dead soft links in the include/linux.

Thanks,
Greg

---

### Post by ggee on 2007-01-28
Well, I figured that your problems probably not the same that I am having.  If you want to use Xen, install Xen 3.0.4 from source on top of Ubuntu 6.06.  I find that 6.10 had too many problems.

The following is what I did to install from a 6.06-amd64-server installation.

2. Install additional packages
apt-get install gs-common libncurses5-dev libncurses5 zlib1g-dev python python-dev python-twisted-core openssl libssl-dev bridge-utils iproute libcurl3 libcurl3-dev bzip2 module-init-tools tetex-base tetex-extra transfig tgif libsdl1.2-dev libvncserver-dev libjpeg-dev qemu bcc bin86
3. Get Xen 3.0.4
wget [http://bits.xensource.com/oss-xen/release/3.0.4-1/src.tgz/xen-3.0.4_1-src.tgz](http://bits.xensource.com/oss-xen/release/3.0.4-1/src.tgz/xen-3.0.4_1-src.tgz)
4. untar/gzip xen package
6. make world
7. make install
8. /sbin/depmod -a 2.6.16.33-xen
9. Edit /etc/mkinitramfs/modules:
loop max_loop=64
10. cd /boot
11. mkinitramfs -o initrd.img-2.6.16.33-xen 2.6.16.33-xen
12. ln -sf initrd.img-2.6.16.33-xen initrd.img-2.6-xen
13. Add to /boot/grub/menu.lst
title           Xen 3.0 / XenLinux 2.6
root            (hd0,0)
kernel          /boot/xen-3.gz console=vga
module          /boot/vmlinuz-2.6-xen root=/dev/sda1 ro
module          /boot/initrd.img-2.6-xen
savedefault
boot


Xen tools:
1.   update-rc.d xend start 30 2 3 4 5 . stop 31 0 1 6 .
2.   update-rc.d xendomains start 31 2 3 4 5 . stop 30 0 1 6 .
3.  Edit /etc/init.d/xend after "/proc/xen/capabilities":

if [ ! -d /var/run/xend ] ; then
    mkdir -p /var/run/xend
fi

if [ ! -d /var/run/xenstored ] ; then
    mkdir -p /var/run/xenstored
fi

4. mv /etc/udev/rules.d/xen-backend.rules /etc/udev/rules.d/92-xen-backend.rules
5.  Edit /etc/init.d/xendomains and replace line:

LOCKFILE=/var/lock/xendomains

  After this, reboot with the new image.  Then look at the following page for installing domU images.

[http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu](http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu)

Greg

---

