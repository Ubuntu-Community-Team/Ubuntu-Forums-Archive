---
title: "Minimal Server Install Support"
date: 2005-10-15
forum: General Help
---

### Post by Tinjaw on 2005-10-15
Hello. I am a veteran Linux user, but brand new to ubuntu. I read that ubuntu had won some awards so I decided to use ubuntu on sandbox server. I grabbed the latest daily build of what I believe is ubuntu server distro. It was dated OCT 13 and I used "linux server" at the boot prompt.

I can't find any wiki page or otherwise that explains what is part of the server distro and what is installed and configured by default. Does such a resource exist? If not, what other places should I look?

thanx,
chaim

---

### Post by zekolas on 2005-10-15
I don't think ubuntu has special server install cd's. Ubuntu just has one install cd(or dvd) for eatch platform supported(eg i386, ppc,amd64). The latest release is 5.10 or Breezy Badger so that is probably what you have.
I believe if you boot the cd you have the option to type in "server" to do a minimal install. Once ubuntu is installed you can use apt-get to install other packages. You can read about 5.10 from here
[http://www.ubuntu.com/newsitems/release510](http://www.ubuntu.com/newsitems/release510)

---

### Post by az on 2005-10-15
About Ubuntu 5.10
-----------------

With this release, the Ubuntu family grows in several significant 
directions:

  * Edubuntu
       A partner distribution based on Ubuntu that is specially
       focused on the needs of schools. Developed in partnership
       with the K12-LTSP community, this is a great base distro
       for people working with FLOSS in schools.  Watch for a
       subsequent announcement with download information for
       Edubuntu.

       [http://www.edubuntu.org/](http://www.edubuntu.org/)

  * Ubuntu for Servers
       This is a CD installer specifically optimised for server 
       installation.  Watch for a subsequent announcement with
       download information for the new Server CD.

I do not know where this cd is.  I cannot find the download link.  I do not think it has been released yet.

You can install a base system withthe regualt install cd.  You get a base system onto which you can install space, postfix or whatever other kind of server you need.  You will need to enable extra repositories to get some packages.

---

### Post by Tinjaw on 2005-10-15
The server download is at:   [http://cdimage.ubuntu.com/ubuntu-server/](http://cdimage.ubuntu.com/ubuntu-server/)

I got the URL from:   [http://www.ubuntu.com/newsitems/release510](http://www.ubuntu.com/newsitems/release510)

That page only gives minimal info:

On the Server

    * Kernel support for cluster filesystems (OCFS2 and GFS)
    * Plone 2.1 & Zope 2.8.1
    * PHP5
    * Support for automatic storage allocation into LVM volumes
    * Built-in thin client functionality produced in cooperation with the LTSP project
    * Simple NFS root setup with automatic hardware detection through initramfs-tools
    * Support for up to 4 gigabytes of RAM by default on 32-bit architectures

---

### Post by patrick295767 on 2005-10-24
Hi, 

Small question on this minima server installation...
Once server ubuntu installed on the harddisk, how much has been installed in general ?
(or approximately ... ) (2GB ?? 300MB?? ..?)
(df -B MB      (i mean))

Someone knows ??

Thank you very much

Best regards

Patrick

---

### Post by mcking on 2005-10-27
A df -h on my fresh server install (from the regular install CD) gives about 356 MB.

I added a 686-smp kernel and openssh-server already, so my package list looks like this:

```

mcking@busted:~$ dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  acpi           0.09-1         displays information on ACPI devices
ii  acpid          1.0.4-1ubuntu8 Utilities for using ACPI power management
ii  adduser        3.64ubuntu1    Add and remove users and groups
ii  alsa-base      1.0.9b-4       ALSA driver configuration files
ii  alsa-utils     1.0.9a-4ubuntu ALSA utilities
ii  apt            0.6.40.1ubuntu Advanced front-end for dpkg
ii  apt-utils      0.6.40.1ubuntu APT utility programs
ii  aptitude       0.2.15.9-3ubun terminal-based apt frontend
ii  at             3.1.8-11ubuntu Delayed job execution and batch processing
ii  base-config    2.67ubuntu19   Debian base system configurator
ii  base-files     3.1.5ubuntu4   Debian base system miscellaneous files
ii  base-passwd    3.5.10         Debian base system master password and group
ii  bash           3.0-16ubuntu3  The GNU Bourne Again SHell
ii  bind9-host     9.3.1-2ubuntu1 Version of 'host' bundled with BIND 9.X
ii  binutils-stati 2.16.1-2ubuntu statically linked binutils tools
ii  bsdmainutils   6.1.2          collection of more utilities from FreeBSD
ii  bsdutils       2.12p-6ubuntu5 Basic utilities from 4.4BSD-Lite
ii  busybox-cvs-in 20040623-1ubun Standalone shell setup for initramfs
ii  bzip2          1.0.2-7ubuntu2 high-quality block-sorting file compressor -
ii  console-common 0.7.51ubuntu1  Basic infrastructure for text console config
ii  console-data   2002.12.04dbs- Keymaps, fonts, charset maps, fallback table
ii  console-tools  0.2.3dbs-56ubu Linux console and font utilities
ii  coreutils      5.2.1-2ubuntu2 The GNU core utilities
ii  cpio           2.5-1.2ubuntu1 GNU cpio -- a program to manage archives of
ii  cron           3.0pl1-87ubunt management of regular background processing
ii  dash           0.5.2-5        The Debian Almquist Shell
ii  debconf        1.4.56ubuntu2  Debian configuration management system
ii  debconf-i18n   1.4.56ubuntu2  full internationalization support for debcon
ii  debianutils    2.14.1-ubuntu2 Miscellaneous utilities specific to Debian
ii  dhcp3-client   3.0.2-1ubuntu6 DHCP Client
ii  dhcp3-common   3.0.2-1ubuntu6 Common files used by all the dhcp3* packages
ii  diff           2.8.1-11ubuntu File comparison utilities
ii  discover1-data 1.2004.11.27ub hardware lists for libdiscover1
ii  dmidecode      2.6-2          Dump Desktop Management Interface data
ii  dmsetup        1.01.03-1ubunt The Linux Kernel Device Mapper userspace lib
ii  dnsutils       9.3.1-2ubuntu1 Clients provided with BIND
ii  dosfstools     2.11-2.1       Utilities to create and check MS-DOS FAT fil
ii  dpkg           1.13.10ubuntu4 Package maintenance system for Debian
ii  dselect        1.13.10ubuntu4 a user tool to manage Debian packages
ii  e2fslibs       1.38-2ubuntu1  ext2 filesystem libraries
ii  e2fsprogs      1.38-2ubuntu1  ext2 file system utilities and libraries
ii  ed             0.2-20         The classic unix line editor
ii  eject          2.0.13deb-13ub ejects CDs and operates CD-Changers under Li
ii  ethtool        2-1            Display or change ethernet card settings
ii  evms           2.5.2-1ubuntu1 Enterprise Volume Management System (core)
ii  evms-ncurses   2.5.2-1ubuntu1 Enterprise Volume Management System (ncurses
ii  fdutils        5.5-20050303-1 Linux floppy utilities
ii  file           4.12-1ubuntu1  Determines file type using "magic" numbers
ii  findutils      4.2.22-2       utilities for finding files--find, xargs, an
ii  ftp            0.17-13        The FTP client
ii  gcc-4.0-base   4.0.1-4ubuntu9 The GNU Compiler Collection (base package)
ii  gettext-base   0.14.5-2ubuntu GNU Internationalization utilities for the b
ii  gnupg          1.4.1-1ubuntu1 GNU privacy guard - a free PGP replacement
ii  grep           2.5.1.ds1-5ubu GNU grep, egrep and fgrep
ii  grepmap        1.0.1-1        Parse module map files produced by depmod
ii  groff-base     1.18.1.1-10    GNU troff text-formatting system (base syste
ii  grub           0.95+cvs200406 GRand Unified Bootloader
ii  gzip           1.3.5-11ubuntu The GNU compression utility
ii  hdparm         6.1-1ubuntu2   tune hard disk parameters for high performan
ii  hostname       2.13           A utility to set/show the host name or domai
ii  hotplug        0.0.20040329-2 Linux Hotplug Scripts
ii  hwdata         0.159-1        hardware identification / configuration data
ii  ifrename       27+28pre8-1ubu Rename network interfaces based on various s
ii  ifupdown       0.6.7ubuntu1   high level tools to configure network interf
ii  info           4.7-2.2ubuntu2 Standalone GNU Info documentation browser
ii  initramfs-tool 0.32           tools for generating an initramfs
ii  initscripts    2.86.ds1-1.1ub Standard scripts needed for booting and shut
ii  installation-r 2.6ubuntu2     system installation report
ii  iproute        20041019-3ubun Professional tools to control the networking
ii  iptables       1.3.1-2ubuntu1 Linux kernel 2.4+ iptables administration to
ii  iputils-arping 20020927-2ubun Tool to send ICMP echo requests to an ARP ad
ii  iputils-ping   20020927-2ubun Tools to test the reachability of network ho
ii  iputils-tracep 20020927-2ubun Tools to trace the network path to a remote
ii  jfsutils       1.1.8-1        utilities for managing the JFS filesystem
ii  klibc-utils    1.0.14-1ubuntu small statically-linked utilities built with
ii  klogd          1.4.1-17ubuntu Kernel Logging Daemon
ii  language-pack- 20051011       translation updates for language English
ii  language-pack- 20051011       translations for language English
ii  less           382-2          Pager program similar to more
ii  libacl1        2.2.29-1       Access control list shared library
ii  libasound2     1.0.9-2        ALSA library
ii  libatm1        2.4.1-17       shared library for ATM (Asynchronous Transfe
ii  libattr1       2.4.21-1       Extended attribute shared library
ii  libbind9-0     9.3.1-2ubuntu1 BIND9 Shared Library used by BIND
ii  libblkid1      1.38-2ubuntu1  block device id library
ii  libbz2-1.0     1.0.2-7ubuntu2 high-quality block-sorting file compressor l
ii  libc6          2.3.5-1ubuntu1 GNU C Library: Shared libraries and Timezone
ii  libc6-i686     2.3.5-1ubuntu1 GNU C Library: Shared libraries [i686 optimi
ii  libcap1        1.10-14        support for getting/setting POSIX.1e capabil
ii  libcomerr2     1.38-2ubuntu1  common error description library
ii  libconsole     0.2.3dbs-56ubu Shared libraries for Linux console and font
ii  libdb1-compat  2.1.3-7        The Berkeley database routines [glibc 2.0/2.
ii  libdb3         3.2.9-22ubuntu Berkeley v3 Database Libraries [runtime]
ii  libdb4.2       4.2.52-19ubunt Berkeley v4.2 Database Libraries [runtime]
ii  libdb4.3       4.3.28-1ubuntu Berkeley v4.3 Database Libraries [runtime]
ii  libdevmapper1. 1.01.03-1ubunt The Linux Kernel Device Mapper userspace lib
ii  libdiscover1   1.7.6ubuntu5   hardware identification library
ii  libdns20       9.3.1-2ubuntu1 DNS Shared Library used by BIND
ii  libedit2       2.9.cvs.200505 BSD editline and history libraries
ii  libelfg0       0.8.5-1        an ELF object file access library
ii  libevms-2.5    2.5.2-1ubuntu1 Enterprise Volume Management System (library
ii  libfribidi0    0.10.5-2       Free Implementation of the Unicode BiDi algo
ii  libgc1c2       6.4-1ubuntu1   conservative garbage collector for C and C++
ii  libgcc1        4.0.1-4ubuntu9 GCC support library
ii  libgcrypt11    1.2.1-3        LGPL Crypto library - runtime library
ii  libgdbm3       1.8.3-2        GNU dbm database routines (runtime version)
ii  libgnutls11    1.0.16-13.1    GNU TLS library - runtime library
ii  libgpg-error0  1.0-1          library for common error values and messages
ii  libgpmg1       1.19.6-20ubunt General Purpose Mouse - shared library
ii  libisc9        9.3.1-2ubuntu1 ISC Shared Library used by BIND
ii  libisccc0      9.3.1-2ubuntu1 Command Channel Library used by BIND
ii  libisccfg1     9.3.1-2ubuntu1 Config File Handling Library used by BIND
ii  libiw28        27+28pre8-1ubu Wireless tools - library
ii  libklibc       1.0.14-1ubuntu minimal libc subset for use with initramfs
ii  libldap2       2.1.30-12      OpenLDAP libraries
ii  liblocale-gett 1.05-1         Using libc functions for internationalizatio
ii  liblwres1      9.3.1-2ubuntu1 Lightweight Resolver Library used by BIND
ii  liblzo1        1.08-2         data compression library
ii  libmagic1      4.12-1ubuntu1  File type determination library using "magic
ii  libncurses5    5.4-9ubuntu4   Shared libraries for terminal handling
ii  libncursesw5   5.4-9ubuntu4   Shared libraries for terminal handling (wide
ii  libnewt0.51    0.51.6-31ubunt Not Erik's Windowing Toolkit - text mode win
ii  libopencdk8    0.5.5-10       Open Crypto Development Kit (OpenCDK) (runti
ii  libpam-modules 0.76-22ubuntu3 Pluggable Authentication Modules for PAM
ii  libpam-runtime 0.76-22ubuntu3 Runtime support for the PAM library
ii  libpam0g       0.76-22ubuntu3 Pluggable Authentication Modules library
ii  libparted1.6-1 1.6.21-1ubuntu The GNU Parted disk partitioning shared libr
ii  libpcap0.8     0.8.3-6        System interface for user-level packet captu
ii  libpopt0       1.7-5          lib for parsing cmdline parameters
ii  libreadline4   4.3-15         GNU readline and history libraries, run-time
ii  libreadline5   5.0-10         GNU readline and history libraries, run-time
ii  libreiserfs0.3 0.3.0.4-4      ReiserFS filesystem access and manipulation
ii  libsasl2       2.1.19-1.5ubun Authentication abstraction library
ii  libsasl2-modul 2.1.19-1.5ubun Pluggable Authentication Modules for SASL
ii  libselinux1    1.24-1         SELinux shared libraries
ii  libsigc++-1.2- 1.2.5-5        type-safe Signal Framework for C++ - runtime
ii  libslang2      2.0.4-4        The S-Lang programming library - runtime ver
ii  libss2         1.38-2ubuntu1  command-line interface parsing library
ii  libssl0.9.7    0.9.7g-1ubuntu SSL shared libraries
ii  libstdc++6     4.0.1-4ubuntu9 The GNU Standard C++ Library v3
ii  libtasn1-2     0.2.10-4       Manage ASN.1 structures (runtime)
ii  libtext-charwi 0.04-2         get display widths of characters on the term
ii  libtext-iconv- 1.4-1          converts between character sets in Perl
ii  libtext-wrapi1 0.06-2         internationalized substitute of Text::Wrap
ii  libusb-0.1-4   0.1.10a-17ubun userspace USB programming library
ii  libuuid1       1.38-2ubuntu1  universally unique id library
ii  libwrap0       7.6.dbs-8      Wietse Venema's TCP wrappers library
ii  linux-386      2.6.12.16      Complete Linux kernel on 386.
ii  linux-686-smp  2.6.12.16      Complete Linux kernel on PPro/Celeron/PII/PI
ii  linux-image-2. 2.6.12-9.23    Linux kernel image for version 2.6.12 on 386
ii  linux-image-2. 2.6.12-9.23    Linux kernel image for version 2.6.12 on PPr
ii  linux-image-38 2.6.12.16      Linux kernel image on 386.
ii  linux-image-68 2.6.12.16      Linux kernel image on PPro/Celeron/PII/PIII/
ii  linux-restrict 2.6.12.4-11    Non-free Linux 2.6.12 modules on 386
ii  linux-restrict 2.6.12.4-11    Non-free Linux 2.6.12 modules on PPro/Celero
ii  linux-restrict 2.6.12.16      Restricted Linux modules on 386.
ii  linux-restrict 2.6.12.16      Restricted Linux modules on PPro/Celeron/PII
ii  linux-restrict 2.6.12.4-11    Non-free Linux 2.6.12 modules helper script
ii  linux-sound-ba 1.0.9b-4       base package for ALSA and OSS sound systems
ii  locales        2.3.5-1ubuntu1 GNU C Library: National Language (locale) da
ii  login          4.0.3-37ubuntu system login tools
ii  logrotate      3.7-5          Log rotation utility
ii  lsb-base       3.0-1ubuntu8   Linux Standard Base 2.0 init script function
ii  lsb-release    1.4-8ubuntu3   LSB release command
ii  lshw           02.03-2build1  information about hardware configuration
ii  lshw-common    02.03-2build1  information about hardware configuration
ii  lsof           4.75.dfsg.1-1  List open files.
ii  ltrace         0.3.36-2       Tracks runtime library calls in dynamically
ii  lvm-common     1.5.17ubuntu1  The Logical Volume Manager for Linux (common
ii  lvm2           2.01.04-5ubunt The Linux Logical Volume Manager
ii  makedev        2.3.1-78ubuntu creates device files in /dev
ii  man-db         2.4.3-3        The on-line manual pager
ii  manpages       2.02-2         Manual pages about using a GNU/Linux system
ii  mawk           1.3.3-11       a pattern scanning and text processing langu
ii  mdadm          1.11.0-0ubuntu Manage MD devices aka Linux Software Raid
ii  memtest86+     1.60-1         thorough real-mode memory tester
ii  mii-diag       2.11-1         A little tool to manipulate network cards
ii  mime-support   3.34-1         MIME files 'mime.types' & 'mailcap', and sup
ii  module-init-to 3.2-pre7-0ubun tools for managing Linux kernel modules
ii  mount          2.12p-6ubuntu5 Tools for mounting and manipulating filesyst
ii  mtr-tiny       0.69-2ubuntu1  Full screen ncurses traceroute tool
ii  nano           1.3.8-2        free Pico clone with some new features
ii  ncurses-base   5.4-9ubuntu4   Descriptions of common terminal types
ii  ncurses-bin    5.4-9ubuntu4   Terminal-related programs and man pages
ii  net-tools      1.60-15ubuntu2 The NET-3 networking toolkit
ii  netbase        4.21ubuntu3    Basic TCP/IP networking system
ii  netcat         1.10-27        TCP/IP swiss army knife
ii  ntpdate        4.2.0a+stable- The ntpdate client for setting system time f
ii  nvidia-kernel- 1.0.7667+1     NVIDIA binary kernel module common files
ii  openssh-client 4.1p1-7ubuntu4 Secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server 4.1p1-7ubuntu4 Secure shell server, an rshd replacement
ii  parted         1.6.21-1ubuntu The GNU Parted disk partition resizing progr
ii  passwd         4.0.3-37ubuntu change and administer password and group dat
ii  pciutils       2.1.11-15ubunt Linux PCI Utilities
ii  perl-base      5.8.7-5ubuntu1 The Pathologically Eclectic Rubbish Lister
ii  popularity-con 1.30ubuntu1    Vote for your favourite packages automatical
ii  ppp            2.4.3-20050321 Point-to-Point Protocol (PPP) daemon
ii  pppconfig      2.3.11ubuntu2  A text menu based utility for configuring pp
ii  pppoeconf      1.8ubuntu2     configures PPPoE/ADSL connections
ii  procps         3.2.5-1ubuntu1 /proc file system utilities
ii  psmisc         21.6-1         Utilities that use the proc filesystem
ii  python         2.4.2-0ubuntu2 An interactive high-level object-oriented la
ii  python-minimal 2.4.2-0ubuntu2 A minimal subset of the Python language (def
ii  python2.4      2.4.2-1        An interactive high-level object-oriented la
ii  python2.4-mini 2.4.2-1        A minimal subset of the Python language (ver
ii  reiser4progs   1.0.4-1ubuntu1 administration utilities for the Reiser4 fil
ii  reiserfsprogs  3.6.19-1       User-level tools for ReiserFS filesystems
ii  reportbug      3.15ubuntu2    Reports bugs in the Debian distribution
ii  rsync          2.6.5-1ubuntu2 fast remote file copy program (like rcp)
ii  sed            4.1.4-2        The GNU sed stream editor
ii  strace         4.5.12-1ubuntu A system call tracer
ii  sudo           1.6.8p9-2ubunt Provide limited super user privileges to spe
ii  sysklogd       1.4.1-17ubuntu System Logging Daemon
ii  sysv-rc        2.86.ds1-1.1ub Standard boot mechanism using symlinks in /e
ii  sysvinit       2.86.ds1-1.1ub System-V like init
ii  tar            1.15.1-2       GNU tar
ii  tcpd           7.6.dbs-8      Wietse Venema's TCP wrapper utilities
ii  tcpdump        3.9.1-1ubuntu1 A powerful tool for network monitoring and d
ii  telnet         0.17-29build1  The telnet client
ii  time           1.7-21         The GNU time program for measuring cpu resou
ii  ubuntu-keyring 2005.01.12.1   GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal 0.80           Minimal core of Ubuntu
ii  ubuntu-standar 0.80           The Ubuntu standard system
ii  udev           0.060-1ubuntu1 /dev/ management daemon
ii  usbutils       0.71-5ubuntu1  USB console utilities
ii  util-linux     2.12p-6ubuntu5 Miscellaneous system utilities
ii  vim            6.3-078+1ubunt Vi IMproved - enhanced vi editor
ii  vim-common     6.3-078+1ubunt Vi IMproved - Common files
ii  w3m            0.5.1-3ubuntu1 WWW browsable pager with excellent tables/fr
ii  wget           1.10-2ubuntu0. retrieves files from the web
ii  whiptail       0.51.6-31ubunt Displays user-friendly dialog boxes from she
ii  wireless-tools 27+28pre8-1ubu Tools for manipulating Linux Wireless Extens
ii  xfsprogs       2.6.28-1       Utilities for managing the XFS filesystem
ii  zlib1g         1.2.3-3ubuntu4 compression library - runtime

```

---

### Post by mcking on 2005-10-27
It looks like the "server" CD is not just the desktop CD without the desktop packages.

See [here]("http://lists.ubuntu.com/archives/ubuntu-announce/2005-October/000042.html").

---

