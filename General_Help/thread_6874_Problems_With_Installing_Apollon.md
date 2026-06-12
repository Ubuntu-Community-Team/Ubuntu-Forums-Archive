---
title: "Problems With Installing Apollon"
date: 2004-12-02
forum: General Help
---

### Post by Satyagraha on 2004-12-02
Hi,

I can't seem to install Apollon. Every time it shows a message "An error occured".

This is what I exactly do to install Apollon:

> sh ./apollon-installer-0.6.run

Then I get this message:

> Verifying archive integrity... All good.
Uncompressing Apollon...........................................................................................
......................................................................................................
......................................................................................................
.....................................................................................................
.................................................................................................... 

It then starts the installation of Apollon. After pressing "Next" twice, it gives an error message and tells me to view my log. This is the log file:

> ***** GiFT
***** Running configure (./configure --prefix=/usr/local)...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... /bin/sed
checking for perl... /usr/bin/perl
checking for xsltproc... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for gethostbyname in -lnsl... yes
checking for socket in -lsocket... no
checking for opendir in -lmingwex... no
checking for inet_ntoa in -lbind... no
checking for openlog in -lbe... no
checking if -lws2_32 is needed... no
checking if -lwsock32 is needed... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking linux/limits.h usability... yes
checking linux/limits.h presence... yes
checking for linux/limits.h... yes
checking for stdint.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking for inttypes.h... (cached) yes
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether byte ordering is bigendian... no
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for void *... yes
checking size of void *... 4
checking for uint8_t... yes
checking for int8_t... yes
checking for uint16_t... yes
checking for int16_t... yes
checking for uint32_t... yes
checking for int32_t... yes
checking for in_addr_t... yes
checking for in_port_t... yes
checking for pid_t... yes
checking for off_t... yes
checking for ssize_t... yes
checking for size_t... yes
checking for getopt... yes
checking for getopt_long... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for ftruncate... yes
checking for gettimeofday... yes
checking for madvise... yes
checking for memdup... no
checking for mkstemp... yes
checking for nice... yes
checking for select... yes
checking for poll... yes
checking for rmdir... yes
checking for signal... yes
checking for socket... yes
checking for socketpair... yes
checking for snprintf... yes
checking for _snprintf... no
checking for vsnprintf... yes
checking for _vsnprintf... no
checking for strcasecmp... yes
checking for strcspn... yes
checking for strlcat... no
checking for strlcpy... no
checking for strmove... no
checking for strpbrk... yes
checking for strspn... yes
checking for strtol... yes
checking for strtoul... yes
checking for unlink... yes
checking for lt_dlopen in -lltdl... no
 * configure: error:
 * *** Couldn't find ltdl library.  If it is installed in a non-standard
 * *** location, please supply --with-ltdl=DIR on the configure command line,
 * *** where `DIR' is the prefix where ltdl is installed (such as /usr,
 * *** /usr/local, or /usr/pkg).  If that doesn't work, check config.log.
 * 
***** Return value 1

Does anybody know what I'm doing wrong?

---

### Post by WW on 2004-12-03
It looks like you need to install the ltdl library (whatever that is).  Try this:```
$ sudo apt-get install libltdl3 libltdl3-dev
```and then run the installation script again.  For future reference, I found these by searching for **ltdl** in Synaptic.  The Search button is a very useful feature.

---

### Post by Satyagraha on 2004-12-05
Thanks for your help! I did what you said, and know I get this in the logview:

> checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... no
checking for libXext... no
 * configure: error: We need a working libXext to proceed. Since configure
 * can't find it itself, we stop here assuming that make wouldn't find
 * them either.
***** Return value 1

What the heck is libXext? I tried to install this package:

> $  sudo apt-get install libXext

But then I get this message:

> Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libXext

So what package do I need now? 

Man, I really hope this program is worth all this trouble!  #-o

---

### Post by WW on 2004-12-05
Either run this command```
$ apt-cache search libXext
``` from the command line, or run Synaptic (Computer->System Configuration->Synaptic Package Manager), click on Search, and enter **libXext** in the "Search:" field.  If you are going to install software from source, you might as well get used to searching for the libraries you need.

In this case, it looks like you might need libxext6 and libxext-dev.  You might not need the -dev package, and you almost certainly don't need the -dbg package.

---

### Post by Satyagraha on 2004-12-07
Man, this program is really giving me a headache! :( I've installed every package it asked for and know I get this error:

```
 * configure: error:
 * in the prefix, you've chosen, are no KDE headers installed. This will fail.
 * So, check this please and use another prefix!
***** Return value 1 
```

What does this mean?

---

### Post by Ste on 2004-12-07
[QUOTE=Satyagraha]Man, this program is really giving me a headache! :( I've installed every package it asked for and know I get this error:

```
 * configure: error:
 * in the prefix, you've chosen, are no KDE headers installed. This will fail.
 * So, check this please and use another prefix!
***** Return value 1 
```

What does this mean?[/QUOTE]

I'm getting the same error when trying to compile kde-bluetooth.
Installed KDE 3.2 this morning and this is the only problem I'm having with it.

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

---

### Post by Satyagraha on 2004-12-08
Well, I dunno how, but I finally managed to install Apollon! :D  But the problems aren't solved yet.  :evil: When I start the program I get an connection error:

```
Connection error

The giFT daemon, which is responsible for connecting to the various networks,
appears to be down and I don't seem to able to start it. Probably your giFT 
installation is corrupted. Try starting giFT manually by typing "giftd" on the
command line. If this gives errors, there's likely some internal error in giFT 
or in your giFT configuration. Refer to the giFT homepage at 
http://giftproject.org for help.
```

When I type "giftd" on the command line, nothing happens.  :confused: So what's wrong now?

---

### Post by p!=f on 2004-12-08
[QUOTE=Satyagraha]
When I type "giftd" on the command line, nothing happens.  :confused: So what's wrong now?[/QUOTE]
What does it mean "nothing happens"? No error? Did the command proceed correctly? Can you see giFT daemon running (ps aux | grep gift)?

---

### Post by Satyagraha on 2004-12-09
Well this exactly what I do:

```
user@user:~ $ giftd
```

I then hit Enter, and it jumps back to:

```
user@user:~ $
```

So, no error message, nothing.  :confused:

---

### Post by p!=f on 2004-12-09
[QUOTE=Satyagraha]Well this exactly what I do:

```
user@user:~ $ giftd
```

I then hit Enter, and it jumps back to:

```
user@user:~ $
```

So, no error message, nothing.  :confused:[/QUOTE]
Try to run
```

giftd &

```
*& means we want to background it*
and then look at the process list if it's running
```

ps aux | grep gift

```
use netstat to see if it's listening on its port
```

sudo netstat -tuanp | grep gift

example:
sudo netstat -tuanp | grep winbindd
tcp        0      0 192.164.171.129:32774   192.164.171.35:445      SPOJENO    3515/winbindd
tcp        0      0 192.164.171.129:32771   192.164.171.35:445      SPOJENO    3515/winbindd
tcp        0      0 192.164.171.129:32806   192.164.171.35:445      SPOJENO    3524/winbindd
tcp        0      0 192.164.171.129:33608   192.164.171.35:445      SPOJENO    3515/winbindd
tcp        0      0 192.164.171.129:33617   172.30.241.77:139       SPOJENO    3515/winbindd
*SPOJENO means CONNECTED*

```

---

### Post by Satyagraha on 2004-12-09
Thanks! That's working. I get this error now:

```
*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/user/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.
``` 

Now that I know what the problem is, I'll try to try fix this later.

Thanks again! 8)

---

### Post by Satyagraha on 2004-12-09
Apollon is working correctly now! :D But, why can't I connect to the OpenFT network? It only connects to the FastTrack and Gnutella network.  :-(

---

### Post by Satyagraha on 2004-12-10
Hey guys,

Apollon is finally working! But (why is there always a "but"  :mad: ), it doesn't connect to the OpenFT network. FastTrack and Gnutella aren't giving any problems, just this one. Is this normal or did I do something wrong?

---

### Post by ibs on 2004-12-29
I am also trying to install this program, when Apollon compiles i get this error:

```

 * /usr/include/kde/kprocess.h:868: internal compiler error: in pop_binding, at 
 *    cp/decl.c:1433
 * Please submit a full bug report,
 * with preprocessed source if appropriate.
 * See <URL:http://gcc.gnu.org/bugs.html> for instructions.
 * For Debian GNU/Linux specific bug reporting instructions, see
 * <URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
 * make[3]: *** [apollonsharedviewtab.o] Error 1
make[3]: Leaving directory `/tmp/selfgz15556/apollon-1.0.1/apollon'
 * make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/selfgz15556/apollon-1.0.1/apollon'
 * make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/selfgz15556/apollon-1.0.1'
 * make: *** [all] Error 2
***** Return value 2

```

What is wrong?

---

### Post by johnmcollier on 2005-04-08
giftd -d

*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/jcollier/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.


[COLOR=DarkOrange]This is what i get after running giftd.. Ive also run the gift-setup about 15 times messing with some of the settings that I wasnt sure about.[/COLOR]

This is what my giftd.conf file looks like:
# $Id: giftd.conf.template,v 1.6 2004/09/08 12:05:32 mkern Exp $
###############################################################################

###############################################################################
# MAIN

[main]

#
# Boolean determining whether or not this file has been reviewed and is
# complete.  giFT will fail to start unless this is non-zero.  This is done
# so that we can make sure you, at the very least, read through this file.
#
# Default: 0
#
setup = 0

#
# Space separated list of hosts to allow connection to giFT's interface
# protocol (running default on port 1213).  This protocol is used for GUIs
# to communicate with giFT and could be considered a security risk to allow
# external connections.
#
# The following special keywords are supported:
#
#  ALL       - Synonym for 0.0.0.0/0
#  LOCAL     - Synonym for 127.0.0.0/8 192.168.0.0/16 172.0.0.0/11 10.0.0.0/8
#
# Bitwidth fields are optional.
#
# Default: LOCAL
#
hosts_allow = all

#
# Port on which to listen for user interface connections.  Unless you have a
# special need to talk to the client on a non-standard port, just accept the
# default.
#
# NOTE:
#  If you change this value, you will also need to modify the ui.conf
#  configuration for the machine which will be making outgoing connections
#  here.
#
client_port = 1213

#
# Determines whether or not to follow symbolic links.  If this value is set
# non-zero, symlinks will be traversed and a directory inode tracking system
# will be used to ensure that giFT does not descend the same directory
# twice.  If you do not have any symlinks or do not want them traversed, set
# this to 0 for a very minor efficiency gain.
#
# Windows users: this setting has no effect.
#
# Default: 1
#
follow_symlinks = 1

#
# Colon separated list of protocol plugins to load by default.  If dynamic
# library support is enabled, the plugin specified will be stat'd to check if
# it is a loadable path.  If that fails, the fallback method is to attempt to
# construct the fully qualified path based on the configured environment.
#
# NOTES:
#  Without dynamic library support, this plugin must have been compiled into
#  your giFT binary.  With, this plugin must exist in the installed
#  plugin directory.  giFT -V will output this path to you, if you are not
#  sure.
#
#  Protocol names are case sensitive, so use OpenFT, not Openft.
#
# For example, to use the OpenFT and Gnutella protocols use:
#
#  OpenFT:Gnutella
#
# Default: none
#
plugins = OpenFT:Gnutella:FastTrack

###############################################################################
# DOWNLOAD CONTROLS

[download]

#
# Directory to store transfers while they are being operated on.  Temporary
# state files are also kept here.  It is recommended, but not required, that
# the incoming and completed directories are on the same partition (drive).
#
# Windows users: please use the following path specification:
#
# incoming=/[drive]/dir1/dir2
#
# For example, to refer to C:\Program Files\giFT\incoming, use:
#
# incoming=/C/Program Files/giFT/incoming
#
# Default (*nix):    ~/.giFT/incoming
# Default (Windows): /C/Program Files/giFT/incoming
#
incoming = /home/jcollier/Downloads/incoming

#
# Directory which will contain files after they have successfully finished
# downloading.
#
# Default (*nix):    ~/.giFT/completed
# Default (Windows): /C/Program Files/giFT/completed
#
completed = /home/jcollier/Downloads

###############################################################################
# SHARE SUBMISSION AND UPLOAD CONTROL

[sharing]

#
# Maximum amount of uploads allowed from the same user at any given time.  It
# is recommended that you keep this at 1 in order to prevent users from
# unfairly queueing your connection.
#
# Default: 1
#
max_peruser_uploads = 1

#
# Determines whether or not to hide directories which contain a leading dot.
# These directories are commonly meant to be "hidden" and thus should not be
# submitted to the network.  Selecting 0 here will submit all directories.
#
# On Windows files will additionally be checked for the hidden attribute and
# not shared if it is set and hide_dot_files is 1.
#
# Default: 1
#
hide_dot_files = 1

#
# Colon separated list of fully qualified paths you wish to share.  These
# directories will be recursed at giFT's startup and the files contained
# within will be subjected to an MD5 hashing.  The results will be cached and
# will only be recalculated on a per share basis when the size or
# modification time in the cache and on disk disagree, or the file name is
# changed.
#
# Sanity notice:
#  Do NOT share source directories!  Remote nodes will refuse to index your
#  shares if you are attempting to submit more than 64000 files.
#
# Security notice:
#  Do not share directories which may contain sensitive information, such as
#  ~ ($HOME).  Also note that any directories shared here will be stripped of
#  all but the last path element when submitted to other nodes for indexing,
#  effectively "hiding" the directory prefix.
#
# Windows users: please use the following path specification:
#
#  /[drive]/dir1/dir2:/[drive]/dir3/dir4 ...
#
# For example, to refer to C:\Program Files\giFT\shares and D:\shares, use:
#
#  /C/Program Files/giFT/shares:/D/shares
#
# Default: none
#
root = /home/jcollier/Downloads

#
# Maximum amount of simultaneous uploads allowed.  Setting this to 0 will
# cause giFT to not limit outgoing transfers.  Use shares_hidden to disable
# sharing.
#
# Default: 0
#
max_uploads = 5

#
# Whether we allow sharing.  Setting this to 0 will allow sharing and uploads
# up to max_uploads.  If this is 1 your shares will be hidden from the world
# and uploading will be denied.  This may also be handled at run time via your
# GUI of choice.
#
# Default: 0
#
shares_hidden = 0

#
# Controls when giFT periodically rescans your shared directories for any
# changes (new files, missing files, changed files, etc.) and communicates
# those changes to the underlying protocols.  This parameter specifies how
# often (in seconds) you want that to happen.
#
# For your reference
# ==================
# 0        turns off periodic auto-resync
# 3600     one hour
# 86400    one day
# 604800   one week
#
# Default: 86400
#
auto_resync_interval = 86400

#
# Controls whether or not giFT should automatically share files that you have
# finished downloading.  This feature significantly improves the network's
# abundance of files and helps ease the load on those sharing popular files.
# It's a Good Thing (TM), please leave it on.
#
# Avoid setting your completed directories through sharing/root, as that
# setting will duplicate recursion of the completed directory and cause
# generally undesirable results.
#
# Default: 1
#
share_completed = 1

#
# Controls whether giFT ignores the incoming directory when sharing files. If
# this is 1 and the incoming directory is within one of the sharing roots all
# files in and below it will not be shared. This is what you want in all known
# universes. Should you find yourself running this software on a parallel
# world where it is necessary to share the incoming files please make sure it
# doesn't affect us back here. Thank you.
#
# Default: 1
#
ignore_incoming = 1

###############################################################################
# USER SPACE BANDWIDTH CONTROL

[bandwidth]

#
# Bandwidth throttling allows giFT to have some basic control over your
# bandwidth usage.  This code operates in user space, and as a result can not
# guarantee perfect accuracy.  If you wish to use this feature, please
# consider using a more reliable kernel space option first.  As always, google
# should be able to assist you there.
#
# The following configuration switches control the maximum number of bytes
# per second allowed for the given stream direction.  A setting of 0 will
# disable throttling for that direction.
#
# Default: 0
#
downstream = 0
upstream = 0

[COLOR=DarkOrange]Please help.  Apollon runs, but giftd wont connect![/COLOR]

---

### Post by NicP on 2005-04-26
[QUOTE=Ste]I'm getting the same error when trying to compile kde-bluetooth.
Installed KDE 3.2 this morning and this is the only problem I'm having with it.

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix![/QUOTE]

how did you guys solve this error?

---

### Post by Hendrik on 2005-05-03
[QUOTE=johnmcollier][COLOR=DarkOrange]This is what i get after running giftd.. Ive also run the gift-setup about 15 times messing with some of the settings that I wasnt sure about.[/COLOR]

This is what my giftd.conf file looks like:
# $Id: giftd.conf.template,v 1.6 2004/09/08 12:05:32 mkern Exp $
###############################################################################

###############################################################################
# MAIN

[main]

#
# Boolean determining whether or not this file has been reviewed and is
# complete. **giFT will fail to start unless this is non-zero.  This is done**
# **so that we can make sure you, at the very least, read through this file.**
#
# Default: 0
#
setup = 0[/QUOTE]

 :roll:

---

### Post by fycloops on 2007-07-22
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

> **NicP said:**
> how did you guys solve this error?

I installed kdebase-dev. Seemed to fo the trick.

Fyc

---

### Post by jindosept on 2007-08-05
Hey, I'm having trouble with apollon as well.  I have it installed, but its not connected to any networks( not sure what they're called, anyway searches don't find anything.)  When I type "apollon" in the terminal I get 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
stimmer@ubuntu:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QGDict::hashKeyString: Invalid null key
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4600269
ICE default IO error handler doing an exit(), pid = 3324, errno = 0

I searched "giftd" in synaptic and installed all the apps.
So does anyone know what's up?

---

