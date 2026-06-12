---
title: "VMWare Install: license key invalid"
date: 2007-07-12
forum: General Help
---

### Post by jamieb22 on 2007-07-12
Hi there

I am busy trying out VMWARE on Ubuntu Feisty. I have followed several different instructions (the canonical  package install, Automatix install, and manual install) with pain staking accuracy and cannot get VMWare to run. When I install the product, it says license key invalid. This occurs even when I copy and paste the license key directly from Vmware's website. I have tried several license keys, quad-druple checked, and still no joy.

I read somewhere that you need to install xlib. In my case xlib is install and so it xlib-dev. I have also installed ia32-libs (on recommendation)

I have a dual core AMD Opteron 2.6 processor machine.
uname -a
2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

There dont seem to be any missing libraries:

root@jamie-desktop:/home/jamie/Desktop/vmware-any-any-update109# ldd /usr/lib/vmware/bin/vmware-vmx
linux-gate.so.1 => (0xffffe000)
libm.so.6 => /lib32/libm.so.6 (0xf7ed3000)
libdl.so.2 => /lib32/libdl.so.2 (0xf7ecf000)
libpthread.so.0 => /lib32/libpthread.so.0 (0xf7eb7000)
libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7dc6000)
libXtst.so.6 => /usr/lib32/libXtst.so.6 (0xf7dc1000)
libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7db3000)
libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d62000)
libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7d4a000)
libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7d40000)
libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7d38000)
libz.so.1 => /usr/lib32/libz.so.1 (0xf7d24000)
libc.so.6 => /lib32/libc.so.6 (0xf7be3000)
/lib/ld-linux.so.2 (0xf7f08000)
libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7be0000)
libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7bdb000)

All the VMWare service startup fine:

Starting VMware services:
Virtual machine monitor done
Virtual ethernet done
Bridged networking on /dev/vmnet0 done
Host-only networking on /dev/vmnet1 (background) done
Host-only networking on /dev/vmnet8 (background) done
NAT service on /dev/vmnet8 done
Starting VMware virtual machines... done

Yet, I cannot enter the license key when I register on VMWare's website. I am using the latest version of the VMWare linux server (VMware-server-1.0.2-39867.tar.gz).

Please help! Any idea why this might be happening and what I need to do to fix it? Is there log output for the VMWare player? The server logs do not show anything unusual.

Many thanks

jamie

---

### Post by lyric0n on 2008-07-11
I am currently experiencing the same issue. I am running Ubuntu 8.04 and VMWare Server 1.06. Any ideas?

---

