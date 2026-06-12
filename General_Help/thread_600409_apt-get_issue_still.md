---
title: "apt-get issue still"
date: 2007-11-02
forum: General Help
---

### Post by devilears on 2007-11-02
Kubuntu Gutsy. I cannot seen to install packages with apt.  apt-get update works fine, but apt-get install runs into this problem:
root@L000021597:~# apt-get install nfs-user-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  portmap
The following packages will be REMOVED:
  gnome-games-data
The following NEW packages will be installed:
  nfs-user-server portmap
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
28 not fully installed or removed.
Need to get 0B/138kB of archives.
After unpacking 27.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 199907 files and directories currently installed.)
Removing gnome-games-data ...
*** glibc detected *** scrollkeeper-update: double free or corruption (!prev): 0x080d8860 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cf2d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cf6800]
/usr/local/cubit/lib/libxml2.so.2(xmlXPathFreeContext+0x4f)[0xb7e4888f]
/usr/lib/libxslt.so.1[0xb7efa295]
/usr/lib/libxslt.so.1[0xb7efaac9]
/usr/lib/libxslt.so.1[0xb7efb0a1]
/usr/lib/libxslt.so.1[0xb7efb786]
/usr/lib/libxslt.so.1(xsltAddTemplate+0x68)[0xb7efbe88]
/usr/lib/libxslt.so.1(xsltParseStylesheetProcess+0x10b2)[0xb7ef4492]
/usr/lib/libxslt.so.1(xsltParseStylesheetImportedDoc+0x1ed)[0xb7ef4b0d]
/usr/lib/libxslt.so.1(xsltParseStylesheetDoc+0x2a)[0xb7ef4bda]
/usr/lib/libxslt.so.1(xsltParseStylesheetFile+0xa7)[0xb7ef4ca7]
/usr/lib/libscrollkeeper.so.0(apply_stylesheets+0x1fe)[0xb7dd645e]
/usr/lib/libscrollkeeper.so.0(install+0x10fe)[0xb7dd842e]
scrollkeeper-update[0x8049d1e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c9f050]
scrollkeeper-update[0x8048f91]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 7184317    /usr/bin/scrollkeeper-update
0804b000-0804c000 rw-p 00002000 08:01 7184317    /usr/bin/scrollkeeper-update
0804c000-0841a000 rw-p 0804c000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0
b7921000-b7a00000 ---p b7921000 00:00 0
b7af3000-b7afd000 r-xp 00000000 08:01 1115135    /lib/libgcc_s.so.1
b7afd000-b7afe000 rw-p 0000a000 08:01 1115135    /lib/libgcc_s.so.1
b7b12000-b7b51000 r--p 00000000 08:01 7258357    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b7b51000-b7c31000 r--p 00000000 08:01 7258356    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b7c31000-b7c33000 rw-p b7c31000 00:00 0
b7c33000-b7c47000 r-xp 00000000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c47000-b7c48000 rw-p 00013000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c48000-b7c5c000 r-xp 00000000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c5c000-b7c5e000 rw-p 00013000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c5e000-b7c60000 rw-p b7c5e000 00:00 0
b7c60000-b7c62000 r-xp 00000000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c62000-b7c64000 rw-p 00001000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c64000-b7c87000 r-xp 00000000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7c87000-b7c89000 rw-p 00023000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7c89000-b7dcd000 r-xp 00000000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7dcd000-b7dce000 r--p 00143000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7dce000-b7dd0000 rw-p 00144000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7dd0000-b7dd3000 rw-p b7dd0000 00:00 0
b7dd3000-b7dda000 r-xp 00000000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7dda000-b7ddb000 rw-p 00007000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7ddb000-b7ddc000 rw-p b7ddb000 00:00 0
b7ddc000-b7ee0000 r-xp 00000000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7ee0000-b7ee9000 rw-p 00103000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7ee9000-b7f1c000 r-xp 00000000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f1c000-b7f1d000 rw-p 00032000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f20000-b7f21000 r--p 00000000 08:01 7258466    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7f21000-b7f22000 r--p 00000000 08:01 7258521    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7f22000-b7f23000 r--p 00000000 08:01 7258422    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7f23000-b7f24000 r--p 00000000 08:01 7258522    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f24000-b7f25000 r--p 00000000 08:01 7258480    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7f25000-b7f26000 r--p 00000000 08:01 7258423    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7f26000-b7f27000 r--p 00000000 08:01 7258424    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7f27000-b7f28000 r--p 00000000 08:01 7258425    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b7f28000-b7f29000 r--p 00000000 08:01 7258476    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b7f29000-b7f30000 r--s 00000000 08:01 7176318    /usr/lib/gconv/gconv-modules.cache
b7f30000-b7f31000 r--p 00000000 08:01 7258426    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7f31000-b7f33000 rw-p b7f31000 00:00 0
b7f33000-b7f4d000 r-xp 00000000 08:01 1114113    /lib/ld-2.6.1.so
b7f4d000-b7f4f000 rw-p 00019000 08:01 1114113    /lib/ld-2.6.1.so
bf95a000-bf970000 rw-p bf95a000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted
dpkg: error processing gnome-games-data (--remove):
 subprocess post-removal script returned error exit status 134
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

What could it be?

---

### Post by mkc on 2007-11-02
I don't understand why to install portmap you have to remove gnome-games ... or infact why gnome-games has installed on Kubuntu! have you tried removing that package separately?

Also I heard that the creaters of apt are recomending aptitude instead of apt-get as a command as it's more advanced, so try "aptitude remove gnome-games-data" and then try installing nfs-user-server again.

---

### Post by devilears on 2007-11-02
Tried aptitude, even more errors:

root@L000021597:~# aptitude remove gnome-games-data
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  gnome-games-data
The following partially installed packages will be configured:
  apturl capplets-data evince-gtk evolution evolution-common evolution-exchange evolution-plugins file-roller gcalctool gcalctool-gtk gdm gnome-app-install
  gnome-control-center gnome-pilot gnome-pilot-conduits gnome-system-monitor gnome-system-tools gucharmap language-selector nautilus restricted-manager
  software-properties-gtk synaptic ubufox update-manager update-notifier zenity
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 28.1MB will be freed.
Writing extended state information... Done
(Reading database ... 199907 files and directories currently installed.)
Removing gnome-games-data ...
*** glibc detected *** scrollkeeper-update: double free or corruption (!prev): 0x08059620 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d09d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d0d800]
/usr/local/cubit/lib/libxml2.so.2(xmlXPathFreeContext+0x4f)[0xb7e5f88f]
/usr/lib/libxslt.so.1[0xb7f11295]
/usr/lib/libxslt.so.1[0xb7f11ac9]
/usr/lib/libxslt.so.1[0xb7f120a1]
/usr/lib/libxslt.so.1[0xb7f12786]
/usr/lib/libxslt.so.1(xsltAddTemplate+0x68)[0xb7f12e88]
/usr/lib/libxslt.so.1(xsltParseStylesheetProcess+0x10b2)[0xb7f0b492]
/usr/lib/libxslt.so.1(xsltParseStylesheetImportedDoc+0x1ed)[0xb7f0bb0d]
/usr/lib/libxslt.so.1(xsltParseStylesheetDoc+0x2a)[0xb7f0bbda]
/usr/lib/libxslt.so.1(xsltParseStylesheetFile+0xa7)[0xb7f0bca7]
/usr/lib/libscrollkeeper.so.0(apply_stylesheets+0x1fe)[0xb7ded45e]
/usr/lib/libscrollkeeper.so.0(install+0x10fe)[0xb7def42e]
scrollkeeper-update[0x8049d1e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cb6050]
scrollkeeper-update[0x8048f91]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 7184317    /usr/bin/scrollkeeper-update
0804b000-0804c000 rw-p 00002000 08:01 7184317    /usr/bin/scrollkeeper-update
0804c000-0841a000 rw-p 0804c000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0
b7a21000-b7b00000 ---p b7a21000 00:00 0
b7b0a000-b7b14000 r-xp 00000000 08:01 1115135    /lib/libgcc_s.so.1
b7b14000-b7b15000 rw-p 0000a000 08:01 1115135    /lib/libgcc_s.so.1
b7b29000-b7b68000 r--p 00000000 08:01 7258357    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b7b68000-b7c48000 r--p 00000000 08:01 7258356    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b7c48000-b7c4a000 rw-p b7c48000 00:00 0
b7c4a000-b7c5e000 r-xp 00000000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c5e000-b7c5f000 rw-p 00013000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c5f000-b7c73000 r-xp 00000000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c73000-b7c75000 rw-p 00013000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c75000-b7c77000 rw-p b7c75000 00:00 0
b7c77000-b7c79000 r-xp 00000000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c79000-b7c7b000 rw-p 00001000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c7b000-b7c9e000 r-xp 00000000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7c9e000-b7ca0000 rw-p 00023000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7ca0000-b7de4000 r-xp 00000000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7de4000-b7de5000 r--p 00143000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7de5000-b7de7000 rw-p 00144000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7de7000-b7dea000 rw-p b7de7000 00:00 0
b7dea000-b7df1000 r-xp 00000000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7df1000-b7df2000 rw-p 00007000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7df2000-b7df3000 rw-p b7df2000 00:00 0
b7df3000-b7ef7000 r-xp 00000000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7ef7000-b7f00000 rw-p 00103000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7f00000-b7f33000 r-xp 00000000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f33000-b7f34000 rw-p 00032000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f37000-b7f38000 r--p 00000000 08:01 7258466    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7f38000-b7f39000 r--p 00000000 08:01 7258521    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7f39000-b7f3a000 r--p 00000000 08:01 7258422    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7f3a000-b7f3b000 r--p 00000000 08:01 7258522    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f3b000-b7f3c000 r--p 00000000 08:01 7258480    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7f3c000-b7f3d000 r--p 00000000 08:01 7258423    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7f3d000-b7f3e000 r--p 00000000 08:01 7258424    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7f3e000-b7f3f000 r--p 00000000 08:01 7258425    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b7f3f000-b7f40000 r--p 00000000 08:01 7258476    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b7f40000-b7f47000 r--s 00000000 08:01 7176318    /usr/lib/gconv/gconv-modules.cache
b7f47000-b7f48000 r--p 00000000 08:01 7258426    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7f48000-b7f4a000 rw-p b7f48000 00:00 0
b7f4a000-b7f64000 r-xp 00000000 08:01 1114113    /lib/ld-2.6.1.so
b7f64000-b7f66000 rw-p 00019000 08:01 1114113    /lib/ld-2.6.1.so
bfbf8000-bfc0d000 rw-p bfbf8000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted
dpkg: error processing gnome-games-data (--remove):
 subprocess post-removal script returned error exit status 134
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gdm (2.20.0-0ubuntu6) ...
 * Reloading GNOME Display Manager configuration...                                                                                                                        * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
*** glibc detected *** scrollkeeper-update: double free or corruption (!prev): 0x0805a678 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d8cd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d90800]
/usr/local/cubit/lib/libxml2.so.2(xmlXPathFreeContext+0x4f)[0xb7ee288f]
/usr/lib/libxslt.so.1[0xb7f94295]
/usr/lib/libxslt.so.1[0xb7f94ac9]
/usr/lib/libxslt.so.1[0xb7f950a1]
/usr/lib/libxslt.so.1[0xb7f95786]
/usr/lib/libxslt.so.1(xsltAddTemplate+0x68)[0xb7f95e88]
/usr/lib/libxslt.so.1(xsltParseStylesheetProcess+0x10b2)[0xb7f8e492]
/usr/lib/libxslt.so.1(xsltParseStylesheetImportedDoc+0x1ed)[0xb7f8eb0d]
/usr/lib/libxslt.so.1(xsltParseStylesheetDoc+0x2a)[0xb7f8ebda]
/usr/lib/libxslt.so.1(xsltParseStylesheetFile+0xa7)[0xb7f8eca7]
/usr/lib/libscrollkeeper.so.0(apply_stylesheets+0x1fe)[0xb7e7045e]
/usr/lib/libscrollkeeper.so.0(install+0x10fe)[0xb7e7242e]
scrollkeeper-update[0x8049d1e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d39050]
scrollkeeper-update[0x8048f91]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 7184317    /usr/bin/scrollkeeper-update
0804b000-0804c000 rw-p 00002000 08:01 7184317    /usr/bin/scrollkeeper-update
0804c000-08418000 rw-p 0804c000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0
b7a21000-b7b00000 ---p b7a21000 00:00 0
b7b8d000-b7b97000 r-xp 00000000 08:01 1115135    /lib/libgcc_s.so.1
b7b97000-b7b98000 rw-p 0000a000 08:01 1115135    /lib/libgcc_s.so.1
b7bac000-b7beb000 r--p 00000000 08:01 7258357    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b7beb000-b7ccb000 r--p 00000000 08:01 7258356    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b7ccb000-b7ccd000 rw-p b7ccb000 00:00 0
b7ccd000-b7ce1000 r-xp 00000000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7ce1000-b7ce2000 rw-p 00013000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7ce2000-b7cf6000 r-xp 00000000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cf6000-b7cf8000 rw-p 00013000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cf8000-b7cfa000 rw-p b7cf8000 00:00 0
b7cfa000-b7cfc000 r-xp 00000000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cfc000-b7cfe000 rw-p 00001000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cfe000-b7d21000 r-xp 00000000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7d21000-b7d23000 rw-p 00023000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7d23000-b7e67000 r-xp 00000000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e67000-b7e68000 r--p 00143000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e68000-b7e6a000 rw-p 00144000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e6a000-b7e6d000 rw-p b7e6a000 00:00 0
b7e6d000-b7e74000 r-xp 00000000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7e74000-b7e75000 rw-p 00007000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7e75000-b7e76000 rw-p b7e75000 00:00 0
b7e76000-b7f7a000 r-xp 00000000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7f7a000-b7f83000 rw-p 00103000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7f83000-b7fb6000 r-xp 00000000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7fb6000-b7fb7000 rw-p 00032000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7fba000-b7fbb000 r--p 00000000 08:01 7258466    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7fbb000-b7fbc000 r--p 00000000 08:01 7258521    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7fbc000-b7fbd000 r--p 00000000 08:01 7258422    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7fbd000-b7fbe000 r--p 00000000 08:01 7258522    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fbe000-b7fbf000 r--p 00000000 08:01 7258480    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7fbf000-b7fc0000 r--p 00000000 08:01 7258423    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7fc0000-b7fc1000 r--p 00000000 08:01 7258424    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7fc1000-b7fc2000 r--p 00000000 08:01 7258425    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b7fc2000-b7fc3000 r--p 00000000 08:01 7258476    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b7fc3000-b7fca000 r--s 00000000 08:01 7176318    /usr/lib/gconv/gconv-modules.cache
b7fca000-b7fcb000 r--p 00000000 08:01 7258426    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7fcb000-b7fcd000 rw-p b7fcb000 00:00 0
b7fcd000-b7fe7000 r-xp 00000000 08:01 1114113    /lib/ld-2.6.1.so
b7fe7000-b7fe9000 rw-p 00019000 08:01 1114113    /lib/ld-2.6.1.so
bfd8b000-bfda1000 rw-p bfd8b000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 134
Setting up gnome-system-monitor (2.20.0-0ubuntu1) ...
*** glibc detected *** scrollkeeper-update: double free or corruption (!prev): 0x080598e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d39d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d3d800]
/usr/local/cubit/lib/libxml2.so.2(xmlXPathFreeContext+0x4f)[0xb7e8f88f]
/usr/lib/libxslt.so.1[0xb7f41295]
/usr/lib/libxslt.so.1[0xb7f41ac9]
/usr/lib/libxslt.so.1[0xb7f420a1]
/usr/lib/libxslt.so.1[0xb7f42786]
/usr/lib/libxslt.so.1(xsltAddTemplate+0x68)[0xb7f42e88]
/usr/lib/libxslt.so.1(xsltParseStylesheetProcess+0x10b2)[0xb7f3b492]
/usr/lib/libxslt.so.1(xsltParseStylesheetImportedDoc+0x1ed)[0xb7f3bb0d]
/usr/lib/libxslt.so.1(xsltParseStylesheetDoc+0x2a)[0xb7f3bbda]
/usr/lib/libxslt.so.1(xsltParseStylesheetFile+0xa7)[0xb7f3bca7]
/usr/lib/libscrollkeeper.so.0(apply_stylesheets+0x1fe)[0xb7e1d45e]
/usr/lib/libscrollkeeper.so.0(install+0x10fe)[0xb7e1f42e]
scrollkeeper-update[0x8049d1e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7ce6050]
scrollkeeper-update[0x8048f91]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 7184317    /usr/bin/scrollkeeper-update
0804b000-0804c000 rw-p 00002000 08:01 7184317    /usr/bin/scrollkeeper-update
0804c000-08429000 rw-p 0804c000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0
b7a21000-b7b00000 ---p b7a21000 00:00 0
b7b3a000-b7b44000 r-xp 00000000 08:01 1115135    /lib/libgcc_s.so.1
b7b44000-b7b45000 rw-p 0000a000 08:01 1115135    /lib/libgcc_s.so.1
b7b59000-b7b98000 r--p 00000000 08:01 7258357    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b7b98000-b7c78000 r--p 00000000 08:01 7258356    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b7c78000-b7c7a000 rw-p b7c78000 00:00 0
b7c7a000-b7c8e000 r-xp 00000000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c8e000-b7c8f000 rw-p 00013000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c8f000-b7ca3000 r-xp 00000000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ca3000-b7ca5000 rw-p 00013000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ca5000-b7ca7000 rw-p b7ca5000 00:00 0
b7ca7000-b7ca9000 r-xp 00000000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca9000-b7cab000 rw-p 00001000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cab000-b7cce000 r-xp 00000000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7cce000-b7cd0000 rw-p 00023000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7cd0000-b7e14000 r-xp 00000000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e14000-b7e15000 r--p 00143000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e15000-b7e17000 rw-p 00144000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7e17000-b7e1a000 rw-p b7e17000 00:00 0
b7e1a000-b7e21000 r-xp 00000000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7e21000-b7e22000 rw-p 00007000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7e22000-b7e23000 rw-p b7e22000 00:00 0
b7e23000-b7f27000 r-xp 00000000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7f27000-b7f30000 rw-p 00103000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7f30000-b7f63000 r-xp 00000000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f63000-b7f64000 rw-p 00032000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7f67000-b7f68000 r--p 00000000 08:01 7258466    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7f68000-b7f69000 r--p 00000000 08:01 7258521    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7f69000-b7f6a000 r--p 00000000 08:01 7258422    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7f6a000-b7f6b000 r--p 00000000 08:01 7258522    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f6b000-b7f6c000 r--p 00000000 08:01 7258480    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7f6c000-b7f6d000 r--p 00000000 08:01 7258423    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7f6d000-b7f6e000 r--p 00000000 08:01 7258424    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7f6e000-b7f6f000 r--p 00000000 08:01 7258425    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b7f6f000-b7f70000 r--p 00000000 08:01 7258476    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b7f70000-b7f77000 r--s 00000000 08:01 7176318    /usr/lib/gconv/gconv-modules.cache
b7f77000-b7f78000 r--p 00000000 08:01 7258426    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7f78000-b7f7a000 rw-p b7f78000 00:00 0
b7f7a000-b7f94000 r-xp 00000000 08:01 1114113    /lib/ld-2.6.1.so
b7f94000-b7f96000 rw-p 00019000 08:01 1114113    /lib/ld-2.6.1.so
bfa61000-bfa76000 rw-p bfa61000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 134
Setting up capplets-data (1:2.20.0.1-0ubuntu5) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince-gtk (2.20.0-0ubuntu3) ...
*** glibc detected *** scrollkeeper-update: double free or corruption (!prev): 0x0805cc28 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7ccad65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cce800]
/usr/local/cubit/lib/libxml2.so.2(xmlXPathFreeContext+0x4f)[0xb7e2088f]
/usr/lib/libxslt.so.1[0xb7ed2295]
/usr/lib/libxslt.so.1[0xb7ed2ac9]
/usr/lib/libxslt.so.1[0xb7ed30a1]
/usr/lib/libxslt.so.1[0xb7ed3786]
/usr/lib/libxslt.so.1(xsltAddTemplate+0x68)[0xb7ed3e88]
/usr/lib/libxslt.so.1(xsltParseStylesheetProcess+0x10b2)[0xb7ecc492]
/usr/lib/libxslt.so.1(xsltParseStylesheetImportedDoc+0x1ed)[0xb7eccb0d]
/usr/lib/libxslt.so.1(xsltParseStylesheetDoc+0x2a)[0xb7eccbda]
/usr/lib/libxslt.so.1(xsltParseStylesheetFile+0xa7)[0xb7eccca7]
/usr/lib/libscrollkeeper.so.0(apply_stylesheets+0x1fe)[0xb7dae45e]
/usr/lib/libscrollkeeper.so.0(install+0x10fe)[0xb7db042e]
scrollkeeper-update[0x8049d1e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c77050]
scrollkeeper-update[0x8048f91]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 7184317    /usr/bin/scrollkeeper-update
0804b000-0804c000 rw-p 00002000 08:01 7184317    /usr/bin/scrollkeeper-update
0804c000-0843a000 rw-p 0804c000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0
b7921000-b7a00000 ---p b7921000 00:00 0
b7acb000-b7ad5000 r-xp 00000000 08:01 1115135    /lib/libgcc_s.so.1
b7ad5000-b7ad6000 rw-p 0000a000 08:01 1115135    /lib/libgcc_s.so.1
b7aea000-b7b29000 r--p 00000000 08:01 7258357    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b7b29000-b7c09000 r--p 00000000 08:01 7258356    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b7c09000-b7c0b000 rw-p b7c09000 00:00 0
b7c0b000-b7c1f000 r-xp 00000000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c1f000-b7c20000 rw-p 00013000 08:01 7179374    /usr/lib/libz.so.1.2.3.3
b7c20000-b7c34000 r-xp 00000000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c34000-b7c36000 rw-p 00013000 08:01 7864389    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c36000-b7c38000 rw-p b7c36000 00:00 0
b7c38000-b7c3a000 r-xp 00000000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c3a000-b7c3c000 rw-p 00001000 08:01 7864348    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c3c000-b7c5f000 r-xp 00000000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7c5f000-b7c61000 rw-p 00023000 08:01 7864349    /lib/tls/i686/cmov/libm-2.6.1.so
b7c61000-b7da5000 r-xp 00000000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7da5000-b7da6000 r--p 00143000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7da6000-b7da8000 rw-p 00144000 08:01 7864343    /lib/tls/i686/cmov/libc-2.6.1.so
b7da8000-b7dab000 rw-p b7da8000 00:00 0
b7dab000-b7db2000 r-xp 00000000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7db2000-b7db3000 rw-p 00007000 08:01 7178067    /usr/lib/libscrollkeeper.so.0.0.0
b7db3000-b7db4000 rw-p b7db3000 00:00 0
b7db4000-b7eb8000 r-xp 00000000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7eb8000-b7ec1000 rw-p 00103000 08:01 7292773    /usr/local/cubit/lib/libxml2.so.2
b7ec1000-b7ef4000 r-xp 00000000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7ef4000-b7ef5000 rw-p 00032000 08:01 7182304    /usr/lib/libxslt.so.1.1.21
b7ef8000-b7ef9000 r--p 00000000 08:01 7258466    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7ef9000-b7efa000 r--p 00000000 08:01 7258521    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7efa000-b7efb000 r--p 00000000 08:01 7258422    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7efb000-b7efc000 r--p 00000000 08:01 7258522    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7efc000-b7efd000 r--p 00000000 08:01 7258480    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7efd000-b7efe000 r--p 00000000 08:01 7258423    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7efe000-b7eff000 r--p 00000000 08:01 7258424    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7eff000-b7f00000 r--p 00000000 08:01 7258425    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b7f00000-b7f01000 r--p 00000000 08:01 7258476    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b7f01000-b7f08000 r--s 00000000 08:01 7176318    /usr/lib/gconv/gconv-modules.cache
b7f08000-b7f09000 r--p 00000000 08:01 7258426    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7f09000-b7f0b000 rw-p b7f09000 00:00 0
b7f0b000-b7f25000 r-xp 00000000 08:01 1114113    /lib/ld-2.6.1.so
b7f25000-b7f27000 rw-p 00019000 08:01 1114113    /lib/ld-2.6.1.so
bffe4000-bfffa000 rw-p bffe4000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
dpkg: error processing evince-gtk (--configure):
 subprocess post-installation script returned error exit status 134
Setting up gnome-pilot (2.0.15-2ubuntu2) ...
dpkg: error processing gnome-pilot (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.20); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.21); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gcalctool (5.20.1-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up synaptic (0.60ubuntu5) ...
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of restricted-manager:
 restricted-manager depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing restricted-manager (--configure):
 dependency problems - leaving unconfigured
Setting up file-roller (2.20.0-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gucharmap (1:1.10.1-0ubuntu1) ...
dpkg: error processing gucharmap (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-system-tools (2.20.0-0ubuntu1) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Setting up zenity (2.20.0-0ubuntu1) ...
dpkg: error processing zenity (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.12.0-0ubuntu5) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-pilot-conduits:
 gnome-pilot-conduits depends on gnome-pilot (>= 2.0.0); however:
  Package gnome-pilot is not configured yet.
dpkg: error processing gnome-pilot-conduits (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcalctool-gtk:
 gcalctool-gtk depends on gcalctool (>= 5.19.4-0ubuntu2); however:
  Package gcalctool is not configured yet.
dpkg: error processing gcalctool-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.12.0-0ubuntu5); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl; however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.11.92); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 gnome-system-monitor
 capplets-data
 evince-gtk
 gnome-pilot
 gnome-control-center
 gcalctool
 synaptic
 restricted-manager
 file-roller
 gucharmap
 nautilus
 gnome-system-tools
 zenity
 evolution-common
 update-manager
 software-properties-gtk
 apturl
 language-selector
 gnome-pilot-conduits
 gnome-app-install
 gcalctool-gtk
 update-notifier
 evolution
 ubufox
 evolution-exchange
 evolution-plugins
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

---

### Post by mkc on 2007-11-06
Okay. You seem to have loads of Gnome packages on your kubuntu setup, and none of them seem to be correctly configured (you probably worked that out but just in case!) Was it a clean install you did to gutsy? when did the problems actually begin?

Try "aptitude -f"  (that is a LOWER case f) according to the man page that "Tries hard to fix the dependencies of broken packages, even if it means ignoring the actions requested on the command line." hopefully if you don't pass any installs etc at the same time it'll just try to fix what's broken. It's worked for me previously using dpkg so maybe it'll fix your problems!

Is there any reason you're using command line utills to do this rather than synaptic? I've found synaptic pretty useful for finding and fixing broken bits previously (they're shown under the  "status" tab)

---

