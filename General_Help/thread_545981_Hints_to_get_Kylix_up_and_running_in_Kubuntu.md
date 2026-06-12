---
title: "Hints to get Kylix up and running in Kubuntu"
date: 2007-09-08
forum: General Help
---

### Post by igoddard on 2007-09-08
The following works for me with Dapper.

If the Athena widgets are not already installed you must install them.  The package is:
libxaw6

Google for ptrace4.tar.gz, download it, make and place the resulting ptrace_interposer.so in /usr/lib (we'll use this library in a minute).

As root issue the command:
echo 1 > /proc/sys/vm/legacy_va_layout

In order to avoid having to do this each time you reboot edit sysctl.conf and add the following line to the end of the file:
vm.legacy_va_layout=1

Without this change autocomplete can't work.

Edit the startdelphi, startbcb and registerkylix files to add:

export LD_ASSUME_KERNEL=2.4.1
export LANG=en_US.ISO8859-1
export LD_PRELOAD=/usr/lib/ptrace_interposer.so

near the start.

The first of these fixes the error message /opt/kylix3/bin/delphi: relocation error: /opt/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

The second fixes the problem that all text is invisible.  For non-English languages see some of the links below for alternative LANG settings and for keyboard mapping.

The third avoids odd debugger behaviour with messages such as:
"received signal SIGTRAP (5). Process stopped. Use Step or Run to continue"

Various Google hits suggest making other library links.  I've found nothing except the above necessary on my system.  There may, however, have been some dependencies which I'd installed prior to installing Kylix.

The fonts are never going to be pretty but editing ~/.borland/.borlandrc will make some improvement to the editor fonts.  In the [Tweak.Layout] section change the WineLook line to:
WineLook=Win95

Useful links:
[http://www.theo.ch/kylix/suse10.html](http://www.theo.ch/kylix/suse10.html)        (Useful for Ubuntu as well as Suse)
[http://www.jsk.com.br/kylix-ubuntu.html](http://www.jsk.com.br/kylix-ubuntu.html)    (in Portuguese!)
[http://andy.jgknet.de/oss/kylix/wiki/index.php/Main_Page](http://andy.jgknet.de/oss/kylix/wiki/index.php/Main_Page)

Ian

---

