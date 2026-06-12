---
title: "convential wisdom of /usr/bin and /usr/local/bin when compiling one's own bin"
date: 2024-01-27
forum: General Help
---

### Post by breakdaze on 2024-01-27
Seems like man hier tries to explain where one traditionally puts binaries. I guess binaries from packages that users can run typically go in /usr/bin but if I download source code, compile, then sudo make install, it probably should go into /usr/local/bin

I know it is just convention, but does that pretty much sound correct?

I downloaded the arm-gnu-toolchain and just threw it in /usr/src but I guess /opt is nice also.

It doesn't matter for using it as long as a bash profile has the path set for the toolchain when I play around with stuff like the Raspberry Pi Pico SDK.

So whatever, really. Opinions?

```
HIER(7)                                                                  Linux Programmer's Manual                                                                  HIER(7)

NAME
       hier - description of the filesystem hierarchy

DESCRIPTION
       A typical Linux system has, among others, the following directories:

       /      This is the root directory.  This is where the whole tree starts.

       /bin   This directory contains executable programs which are needed in single user mode and to bring the system up or repair it.

       /boot  Contains  static  files for the boot loader.  This directory holds only the files which are needed during the boot process.  The map installer and configura&#8208;
              tion files should go to /sbin and /etc.  The operating system kernel (initrd for example) must be located in either / or /boot.

       /dev   Special or device files, which refer to physical devices.  See mknod(1).

       /etc   Contains configuration files which are local to the machine.  Some larger software packages, like X11, can have their own subdirectories below  /etc.   Site-
              wide  configuration  files  may  be placed here or in /usr/etc.  Nevertheless, programs should always look for these files in /etc and you may have links for
              these files to /usr/etc.

       /etc/opt
              Host-specific configuration files for add-on applications installed in /opt.

       /etc/sgml
              This directory contains the configuration files for SGML (optional).

       /etc/skel
              When a new user account is created, files from this directory are usually copied into the user's home directory.

       /etc/X11
              Configuration files for the X11 window system (optional).

       /etc/xml
              This directory contains the configuration files for XML (optional).

       /home  On machines with home directories for users, these are usually beneath this directory, directly or not.  The structure of this directory depends on local ad&#8208;
              ministration decisions (optional).

       /lib   This directory should hold those shared libraries that are necessary to boot the system and to run the commands in the root filesystem.

       /lib<qual>
              These directories are variants of /lib on system which support more than one binary format requiring separate libraries (optional).

       /lib/modules
              Loadable kernel modules (optional).

       /lost+found
              This directory contains items lost in the filesystem.  These items are usually chunks of files mangled as a consequence of a faulty disk or a system crash.

       /media This directory contains mount points for removable media such as CD and DVD disks or USB sticks.  On systems where more than one device exists for mounting a
              certain type of media, mount directories can be created by appending a digit to the name of those available above starting with '0', but the unqualified name
              must also exist.

       /media/floppy[1-9]
              Floppy drive (optional).

       /media/cdrom[1-9]
              CD-ROM drive (optional).

       /media/cdrecorder[1-9]
              CD writer (optional).

       /media/zip[1-9]
              Zip drive (optional).

       /media/usb[1-9]
              USB drive (optional).

       /mnt   This  directory  is  a  mount  point  for a temporarily mounted filesystem.  In some distributions, /mnt contains subdirectories intended to be used as mount
              points for several temporary filesystems.

       /opt   This directory should contain add-on packages that contain static files.

       /proc  This is a mount point for the proc filesystem, which provides information about running processes and the kernel.  This  pseudo-filesystem  is  described  in
              more detail in proc(5).

       /root  This directory is usually the home directory for the root user (optional).

       /run   This  directory  contains  information which describes the system since it was booted.  Once this purpose was served by /var/run and programs may continue to
              use it.

       /sbin  Like /bin, this directory holds commands needed to boot the system, but which are usually not executed by normal users.

       /srv   This directory contains site-specific data that is served by this system.

       /sys   This is a mount point for the sysfs filesystem, which provides information about the kernel like /proc, but better structured,  following  the  formalism  of
              kobject infrastructure.

       /tmp   This directory contains temporary files which may be deleted with no notice, such as by a regular job or at system boot up.

       /usr   This  directory  is  usually mounted from a separate partition.  It should hold only shareable, read-only data, so that it can be mounted by various machines
              running Linux.

       /usr/X11R6
              The X-Window system, version 11 release 6 (present in FHS 2.3, removed in FHS 3.0).

       /usr/X11R6/bin
              Binaries which belong to the X-Window system; often, there is a symbolic link from the more traditional /usr/bin/X11 to here.

       /usr/X11R6/lib
              Data files associated with the X-Window system.

       /usr/X11R6/lib/X11
              These contain miscellaneous files needed to run X;  Often, there is a symbolic link from /usr/lib/X11 to this directory.

       /usr/X11R6/include/X11
              Contains include files needed for compiling programs using the X11 window system.  Often, there is a symbolic link from /usr/include/X11 to this directory.

       /usr/bin
              This is the primary directory for executable programs.  Most programs executed by normal users which are not needed for booting or for repairing  the  system
              and which are not installed locally should be placed in this directory.

       /usr/bin/mh
              Commands for the MH mail handling system (optional).

       /usr/bin/X11
              This is the traditional place to look for X11 executables; on Linux, it usually is a symbolic link to /usr/X11R6/bin.

       /usr/dict
              Replaced by /usr/share/dict.

       /usr/doc
              Replaced by /usr/share/doc.

       /usr/etc
              Site-wide  configuration  files to be shared between several machines may be stored in this directory.  However, commands should always reference those files
              using the /etc directory.  Links from files in /etc should point to the appropriate files in /usr/etc.

       /usr/games
              Binaries for games and educational programs (optional).

       /usr/include
              Include files for the C compiler.

       /usr/include/bsd
              BSD compatibility include files (optional).

       /usr/include/X11
              Include files for the C compiler and the X-Window system.  This is usually a symbolic link to /usr/X11R6/include/X11.

       /usr/include/asm
              Include files which declare some assembler functions.  This used to be a symbolic link to /usr/src/linux/include/asm.

       /usr/include/linux
              This contains information which may change from system release to system release and used to be a symbolic link to /usr/src/linux/include/linux to get at op&#8208;
              erating-system-specific information.

              (Note  that one should have include files there that work correctly with the current libc and in user space.  However, Linux kernel source is not designed to
              be used with user programs and does not know anything about the libc you are using.  It is very likely that things will break if you let /usr/include/asm and
              /usr/include/linux  point  at a random kernel tree.  Debian systems don't do this and use headers from a known good kernel version, provided in the libc*-dev
              package.)

       /usr/include/g++
              Include files to use with the GNU C++ compiler.

       /usr/lib
              Object libraries, including dynamic libraries, plus some executables which usually are not invoked directly.  More complicated programs may have whole subdi&#8208;
              rectories there.

       /usr/libexec
              Directory contains binaries for internal use only and they are not meant to be executed directly by users shell or scripts.

       /usr/lib<qual>
              These  directories  are  variants of /usr/lib on system which support more than one binary format requiring separate libraries, except that the symbolic link
              /usr/lib<qual>/X11 is not required (optional).

       /usr/lib/X11
              The usual place for data files associated with X programs, and configuration files for the X system itself.  On Linux, it  usually  is  a  symbolic  link  to
              /usr/X11R6/lib/X11.

       /usr/lib/gcc-lib
              contains executables and include files for the GNU C compiler, gcc(1).

       /usr/lib/groff
              Files for the GNU groff document formatting system.

       /usr/lib/uucp
              Files for uucp(1).

       /usr/local
              This is where programs which are local to the site typically go.

       /usr/local/bin
              Binaries for programs local to the site.

       /usr/local/doc
              Local documentation.

       /usr/local/etc
              Configuration files associated with locally installed programs.

       /usr/local/games
              Binaries for locally installed games.

       /usr/local/lib
              Files associated with locally installed programs.

       /usr/local/lib<qual>
              These directories are variants of /usr/local/lib on system which support more than one binary format requiring separate libraries (optional).

       /usr/local/include
              Header files for the local C compiler.

       /usr/local/info
              Info pages associated with locally installed programs.

       /usr/local/man
              Man pages associated with locally installed programs.

       /usr/local/sbin
              Locally installed programs for system administration.

       /usr/local/share
              Local application data that can be shared among different architectures of the same OS.

       /usr/local/src
              Source code for locally installed software.

       /usr/man
              Replaced by /usr/share/man.

       /usr/sbin
              This directory contains program binaries for system administration which are not essential for the boot process, for mounting /usr, or for system repair.

       /usr/share
              This  directory  contains  subdirectories  with  specific application data, that can be shared among different architectures of the same OS.  Often one finds
              stuff here that used to live in /usr/doc or /usr/lib or /usr/man.

       /usr/share/color
              Contains color management information, like International Color Consortium (ICC) Color profiles (optional).

       /usr/share/dict
              Contains the word lists used by spell checkers (optional).

       /usr/share/dict/words
              List of English words (optional).

       /usr/share/doc
              Documentation about installed programs (optional).

       /usr/share/games
              Static data files for games in /usr/games (optional).

       /usr/share/info
              Info pages go here (optional).

       /usr/share/locale
              Locale information goes here (optional).

       /usr/share/man
              Manual pages go here in subdirectories according to the man page sections.

       /usr/share/man/<locale>/man[1-9]
              These directories contain manual pages for the specific locale in source code form.  Systems which use a unique language and code set for  all  manual  pages
              may omit the <locale> substring.

       /usr/share/misc
              Miscellaneous data that can be shared among different architectures of the same OS.

       /usr/share/nls
              The message catalogs for native language support go here (optional).

       /usr/share/ppd
              Postscript Printer Definition (PPD) files (optional).

       /usr/share/sgml
              Files for SGML (optional).

       /usr/share/sgml/docbook
              DocBook DTD (optional).

       /usr/share/sgml/tei
              TEI DTD (optional).

       /usr/share/sgml/html
              HTML DTD (optional).

       /usr/share/sgml/mathtml
              MathML DTD (optional).

       /usr/share/terminfo
              The database for terminfo (optional).

       /usr/share/tmac
              Troff macros that are not distributed with groff (optional).

       /usr/share/xml
              Files for XML (optional).

       /usr/share/xml/docbook
              DocBook DTD (optional).

       /usr/share/xml/xhtml
              XHTML DTD (optional).

       /usr/share/xml/mathml
              MathML DTD (optional).

       /usr/share/zoneinfo
              Files for timezone information (optional).

       /usr/src
              Source  files  for different parts of the system, included with some packages for reference purposes.  Don't work here with your own projects, as files below
              /usr should be read-only except when installing software (optional).

       /usr/src/linux
              This was the traditional place for the kernel source.  Some distributions put here the source for the default kernel they ship.  You should probably use  an&#8208;
              other directory when building your own kernel.

       /usr/tmp
              Obsolete.  This should be a link to /var/tmp.  This link is present only for compatibility reasons and shouldn't be used.

       /var   This directory contains files which may change in size, such as spool and log files.

       /var/account
              Process accounting logs (optional).

       /var/adm
              This directory is superseded by /var/log and should be a symbolic link to /var/log.

       /var/backups
              Reserved for historical reasons.

       /var/cache
              Data cached for programs.

       /var/cache/fonts
              Locally generated fonts (optional).

       /var/cache/man
              Locally formatted man pages (optional).

       /var/cache/www
              WWW proxy or cache data (optional).

       /var/cache/<package>
              Package specific cache data (optional).

       /var/catman/cat[1-9] or /var/cache/man/cat[1-9]
              These directories contain preformatted manual pages according to their man page section.  (The use of preformatted manual pages is deprecated.)

       /var/crash
              System crash dumps (optional).

       /var/cron
              Reserved for historical reasons.

       /var/games
              Variable game data (optional).

       /var/lib
              Variable state information for programs.

       /var/lib/color
              Variable files containing color management information (optional).

       /var/lib/hwclock
              State directory for hwclock (optional).

       /var/lib/misc
              Miscellaneous state data.

       /var/lib/xdm
              X display manager variable data (optional).

       /var/lib/<editor>
              Editor backup files and state (optional).

       /var/lib/<name>
              These directories must be used for all distribution packaging support.

       /var/lib/<package>
              State data for packages and subsystems (optional).

       /var/lib/<pkgtool>
              Packaging support files (optional).

       /var/local
              Variable data for /usr/local.

       /var/lock
              Lock files are placed in this directory.  The naming convention for device lock files is LCK..<device> where <device> is the device's name in the filesystem.
              The format used is that of HDU UUCP lock files, that is, lock files contain a PID as a 10-byte ASCII decimal number, followed by a newline character.

       /var/log
              Miscellaneous log files.

       /var/opt
              Variable data for /opt.

       /var/mail
              Users' mailboxes.  Replaces /var/spool/mail.

       /var/msgs
              Reserved for historical reasons.

       /var/preserve
              Reserved for historical reasons.

       /var/run
              Run-time variable files, like files holding process identifiers (PIDs) and logged user information (utmp).  Files in this directory are usually cleared  when
              the system boots.

       /var/spool
              Spooled (or queued) files for various programs.

       /var/spool/at
              Spooled jobs for at(1).

       /var/spool/cron
              Spooled jobs for cron(8).

       /var/spool/lpd
              Spooled files for printing (optional).

       /var/spool/lpd/printer
              Spools for a specific printer (optional).

       /var/spool/mail
              Replaced by /var/mail.

       /var/spool/mqueue
              Queued outgoing mail (optional).

       /var/spool/news
              Spool directory for news (optional).

       /var/spool/rwho
              Spooled files for rwhod(8) (optional).

       /var/spool/smail
              Spooled files for the smail(1) mail delivery program.

       /var/spool/uucp
              Spooled files for uucp(1) (optional).

       /var/tmp
              Like /tmp, this directory holds temporary files stored for an unspecified duration.

       /var/yp
              Database files for NIS, formerly known as the Sun Yellow Pages (YP).

CONFORMING TO
       The Filesystem Hierarchy Standard (FHS), Version 3.0, published March 19, 2015 &#10216;https://refspecs.linuxfoundation.org/fhs.shtml&#10217;.

BUGS
       This list is not exhaustive; different distributions and systems may be configured differently.

SEE ALSO
       find(1), ln(1), proc(5), file-hierarchy(7), mount(8)

       The Filesystem Hierarchy Standard

COLOPHON
       This  page  is  part of release 5.13 of the Linux man-pages project.  A description of the project, information about reporting bugs, and the latest version of this
       page, can be found at https://www.kernel.org/doc/man-pages/.

Linux                                                                            2021-03-22                                                                         HIER(7)

```

---

### Post by TheFu on 2024-01-27
Linux Hierarchy Standards Document is the reference.  [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)

> 4.9. /usr/local : Local hierarchy
4.9.1. Purpose

The /usr/local hierarchy is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr.

Locally installed software must be placed within /usr/local rather than /usr unless it is being installed to replace or upgrade software in /usr. [28] 

So, anything outside the distros package manager can be installed there.  However, I place commercial software under /opt/ and only F/LOSS under /usr/local/

BTW, be certain to read about what belongs in /media/   - most Linux distros violate the standard by mounting USB HDDs there.  Snap packages also violate a number of standards, but that a fight that can only be won by switching distros.

I think /bin/ and /usr/bin/ are being merged.  Probably the same for /sbin/ and /usr/sbin/.  I'm not a fan of this choice - /bin/ should be CLI programs core to the OS.  /usr/bin/ should be extra programs and GUI programs, both installed using the package manager.

Lastly, be 100% certain that your backups include /usr/local/.   I don't bother backing up package installed stuff. I do get /usr/local/ and /etc/ along with a list of manually installed packages through APT.

---

### Post by breakdaze on 2024-01-27
Great, thanks for the detailed explanation.

I compiled a gcc cross-compiler for an arm target and the GNU docs seem to say the default install prefix is /usr/local so I think I'm good there.

Good idea about /opt being used for commercial stuff.

---

### Post by breakdaze on 2024-01-27
A related question, I downloaded the latest pre-built cross-compiler toolchain for bare metal target running on Linux x_86 host: x86_64 Linux hosted cross toolchains
AArch32 bare-metal target (arm-none-eabi) from here [https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)

Extracting it gives a tree like

```
find /usr/src/arm-gnu-toolchain -maxdepth 1 -type d -printf "%P/\n"
/
share/
arm-none-eabi/
include/
bin/
lib/
libexec/

```

Then I'm using the Raspberry Pi Pico SDK to develop for the Raspberry Pi Pico ARM microcontroller, so I threw the entire thing under /usr/src

Then to use the SDK I have an export to the required path for the toolchain as used by their SDK: PICO_TOOLCHAIN_PATH=/usr/src/arm-gnu-toolchain

I guess /usr/src works, it is also where the Linux kernel sources are as well as openocd sources that I used to build openocd.

What do you do?

---

### Post by TheFu on 2024-01-27
I've never done embedded programming in C.  All my embedded stuff used environments that were managed by teams of experts in the custom compilers, custom version control system and OSes involved.  We did cross compile for different hardware.  I never touched the development computer nor the actual hardware it ran on while it was running. My clearance didn't allow that.  If you care, we used a language called HAL/S. [https://en.wikipedia.org/wiki/HAL/S](https://en.wikipedia.org/wiki/HAL/S)

However, I wouldn't pollute system code in /usr/src with anything I developed.  I'd have my development performed in my HOME 99% of the time. If I was working in a team,  I'd push my libraries and headers to a central location at a specific time daily. Each team member would do the same, to limit disruptions for each other, but also not be too far behind each other or require everyone to build the libraries for themselves.  I worked on cross-platform development teams with 3-30 people using this method for about a decade.  We were careful about the dependencies for each library to prevent circular dependencies.  On one project, when I was first hired, their dependencies were a mess. They had to try to build the system 3 times because they wouldn't be able to resolve all the different dependencies.  The entire team spent a week reworking our libraries just for cleaner dependencies for the different clients and servers.  It was a 4-Tier architecture that allowed mixing and matching any of the different tiers on any supported platform. Our customers appreciated that we could use a DBMS on an IBM P-Series, have our data layer on a Solaris system and the application layer on an HP, with the clients being Windows (typically) or SGI (sometimes).

Alas, it was a different time.

---

### Post by SeijiSensei on 2024-01-27
I use /usr/local for anything I install outside the repository system. These days that's not many items. Back when I would compile programs from scratch (e.g., sendmail, bind, etc.) I would put the source in /usr/local/src, and by default the binaries and configuration files would be placed in /usr/local/bin, /usr/local/sbin, /usr/local/lib, and /usr/local/etc. I put admin scripts in /usr/local/sbin. For instance, my backup script in /usr/local/sbin uses files in /usr/local/etc.

---

### Post by TheFu on 2024-01-27
> **SeijiSensei said:**
> I use /usr/local for anything I install outside the repository system. These days that's not many items. Back when I would compile programs from scratch (e.g., sendmail, bind, etc.) I would put the source in /usr/local/src, and by default the binaries and configuration files would be placed in /usr/local/bin, /usr/local/sbin, /usr/local/lib, and /usr/local/etc. I put admin scripts in /usr/local/sbin. For instance, my backup script in /usr/local/sbin uses files in /usr/local/etc.

+1 for all of this.

I also put AppImages under /usr/local/appimage/  Just to have them in a central place and included in my backups.

---

### Post by breakdaze on 2024-01-28
@TheFu, wow crazy times indeed! Embedded programming has never been easier, and the Pico is dirt cheap. There is even a Wifi version. About ~ $6 USD.

@SeijiSensei Cool beans. Yeah, I have been just compiling somewhere in $HOME/src then just running su to do the make install part. Mostly GNU stuff, and that happens to install to the prefix /usr/local  The pre-built toolchain, however was subjective, but I agree /usr/local/* is a good place. Thanks for the input.

---

