---
title: "Compiling AMANDA from source"
date: 2007-01-16
forum: General Help
---

### Post by Justin Trouble on 2007-01-16
Hi all!
The Edgy/6.10 AMANDA (2.5.0.p2) package is not compatible with the Edgy/6.10 version of tar!

I'm planning to compile the AMANDA source package (from Feisty - AMANDA version 2.5.1p1).

AMANDA requires several build (./configure) parameters.

Can anyone tell me how I can find the ./configure parameters used for the official Ubuntu/Debian AMANDA packages?

Many thanks! Justin

---

### Post by Sqwishy on 2007-01-16
Wait are you saying that you ran ./configure and it say'd that you needed certain packages/dependacies? Did it give any output that you could show?

---

### Post by Justin Trouble on 2007-01-16
> **Sqwishy said:**
> Wait are you saying that you ran ./configure and it say'd that you needed certain packages/dependacies? Did it give any output that you could show?

Hi! Thanks for your reply.
It's not dependencies, it's configuration options for the AMANDA program. 

For example (some I picked out)...
  --with-dumperdir=DIR   where we install the dumpers [EPREFIX/dumper]
  --with-configdir=DIR   runtime config files in DIR [sysconfdir/amanda]
  --with-indexdir        deprecated, use indexdir in amanda.conf
  --with-dbdir           deprecated, use infofile in amanda.conf
  --with-logdir          deprecated, use logfile in amanda.conf
  --with-suffixes        install binaries with version string appended to name
  --with-index-server=HOST default amanda index server [`uname -n`]
  --without-force-uid    do not force the uid to --with-user
  --with-user=USER       force execution to USER on client systems [required]
  --with-group=GROUP     group allowed to execute setuid-root programs [required]
  --with-owner=USER       force ownership of files to USER [default == --with-user value]
  --with-rundump         use rundump (setuid-root) to invoke dump
  --with-config=CONFIG   default configuration [DailySet1]

I wanted to use a standard user and group and put all the configuration, log, db and index files in a standard place (as far as Ubuntu is concerned).

---

### Post by Sqwishy on 2007-01-16
oh yeah i've seen that before, but it's a little bit too complicated for me to figure out. did you look on documention on the AMANDA site

---

### Post by Justin Trouble on 2007-01-16
> **Sqwishy said:**
> oh yeah i've seen that before, but it's a little bit too complicated for me to figure out. did you look on documention on the AMANDA site

Well I could work it out myself with a bit of time, but it's far easier to know the build/configure options used with the Ubuntu/Debian package!

That information isn't stored in the .deb somewhere is it?

---

### Post by Sqwishy on 2007-01-16
I don't know . . . :-|

---

### Post by Justin Trouble on 2007-01-18
I worked it out myself.

I installed the current (old, incompatible*) version Ubuntu amanda-client package.
Ran /usr/lib/amanda/amandad, then ctrl-c'd it.

Then looked in the amandad log file (E.g./var/log/amanda/amandad.20070118135507.debug)  which includes the build options.

The build options for version 2.5.0p2 of the Ubuntu Amanda client (amanda-client) package are:
./configure' '--prefix=/usr' '--bindir=/usr/sbin' '--mandir=/usr/share/man' --libexecdir=/usr/lib/amanda' '--enable-shared' '--sysconfdir=/etc' '--localstatedir=/var/lib' '--with-gnutar-listdir=/var/lib/amanda/gnutar-lists' '--with-index-server=localhost' '--with-user=backup' '--with-group=backup' '--with-bsd-security' '--with-amandahosts' '--with-smbclient=/usr/bin/smbclient' '--with-debugging=/var/log/amanda' '--with-dumperdir=/usr/lib/amanda/dumper.d' '--with-tcpportrange=50000,50100' '--with-udpportrange=840,860' '--with-maxtapeblocksize=256'


The start of the amandad log file in full:

build: VERSION="Amanda-2.5.0p2"
       BUILT_DATE="Wed Jun 21 01:46:12 UTC 2006"
       BUILT_MACH="Linux vernadsky 2.6.12 #1 SMP Mon Jan 2 16:52:14 UTC 2006 i686 GNU/Linux"
       CC="gcc"
       CONFIGURE_COMMAND="'./configure' '--prefix=/usr' '--bindir=/usr/sbin' '--mandir=/usr/share/man' --libexecdir=/usr/lib/amanda' '--enable-shared' '--sysconfdir=/etc' '--localstatedir=/var/lib' '--with-gnutar-listdir=/var/lib/amanda/gnutar-lists' '--with-index-server=localhost' '--with-user=backup' '--with-group=backup' '--with-bsd-security' '--with-amandahosts' '--with-smbclient=/usr/bin/smbclient' '--with-debugging=/var/log/amanda' '--with-dumperdir=/usr/lib/amanda/dumper.d' '--with-tcpportrange=50000,50100' '--with-udpportrange=840,860' '--with-maxtapeblocksize=256'"
paths: bindir="/usr/sbin" sbindir="/usr/sbin"
       libexecdir="/usr/lib/amanda" mandir="/usr/share/man"
       AMANDA_TMPDIR="/tmp/amanda"
       AMANDA_DBGDIR="/var/log/amanda" CONFIG_DIR="/etc/amanda"
       DEV_PREFIX="/dev/" RDEV_PREFIX="/dev/" DUMP="/sbin/dump"
       RESTORE="/sbin/restore" VDUMP=UNDEF VRESTORE=UNDEF
       XFSDUMP="/sbin/xfsdump" XFSRESTORE="/sbin/xfsrestore"
       VXDUMP=UNDEF VXRESTORE=UNDEF SAMBA_CLIENT=UNDEF
       GNUTAR="/bin/tar" COMPRESS_PATH="/bin/gzip"
       UNCOMPRESS_PATH="/bin/gzip" LPRCMD="/usr/bin/lpr"
       MAILER="/usr/bin/mail"
       listed_incr_dir="/var/lib/amanda/gnutar-lists"
defs:  DEFAULT_SERVER="localhost" DEFAULT_CONFIG="DailySet1"
       DEFAULT_TAPE_SERVER="localhost"
       DEFAULT_TAPE_DEVICE="null:" HAVE_MMAP HAVE_SYSVSHM
       LOCKING=POSIX_FCNTL SETPGRP_VOID DEBUG_CODE
       AMANDA_DEBUG_DAYS=4 BSD_SECURITY RSH_SECURITY USE_AMANDAHOSTS
       CLIENT_LOGIN="backup" FORCE_USERID HAVE_GZIP
       COMPRESS_SUFFIX=".gz" COMPRESS_FAST_OPT="--fast"
       COMPRESS_BEST_OPT="--best" UNCOMPRESS_OPT="-dc"


* Tar (GNU tar) 1.15.91 is not fully compatible with this version 2.5.0p2 of AMANDA.

See "Amanda-client: upgrading tar breaks incremental backups" - [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=378558](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=378558)

Compatibility with tar (GNU tar) 1.15.91 was added in the 2.5.1 beta 1 release.

---

### Post by dgrincletus on 2007-01-21
All of the build options you listed are also listed in the file [amanda_2.5.0p2-1.diff.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/a/amanda/amanda_2.5.0p2-1.diff.gz"). There is a link to this file on the amanda-client package page (near the bottom in the 'More Information on amanda-client' section. Just open up the file and search for './configure'.

I would assume that one should be able to get the build options for most packages by searching through the appropriate diff file.

---

