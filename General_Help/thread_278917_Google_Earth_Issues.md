---
title: "Google Earth Issues"
date: 2006-10-17
forum: General Help
---

### Post by hvc123 on 2006-10-17
Hi all, 

hope someone can help im really stuck. Google Earth starts then crashes with this 
" ./googleearth-bin: ./libpng12.so.0: no version information available (required by ./libqt-mt.so.3)
Google Earth has caught signal 8.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x21e) [0x804ab52]
  ./googleearth-bin [0x804b153]
  [0xffffe420]
  ./libqt-mt.so.3 [0xb6f0877f]
  ./libqt-mt.so.3(_ZN12QPaintDevice10x11AppDpiYEi+0x17) [0xb6f08a07]
  ./libqt-mt.so.3(_ZN12QPaintDevice10x11AppDpiYEv+0x1e) [0xb6f08a84]
  ./libqt-mt.so.3(_Z16qt_init_internalPiPPcP9_XDisplaymm+0x21ce) [0xb6ee2ad2]
  ./libqt-mt.so.3(_Z7qt_initPiPPcN12QApplication4TypeE+0x3c) [0xb6ee35f4]
  ./libqt-mt.so.3(_ZN12QApplication9constructERiPPcNS_4TypeE+0x86) [0xb6f582d2]
  ./libqt-mt.so.3(_ZN12QApplicationC1ERiPPc+0x6a) [0xb6f58682]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0xde) [0xb78a67ae]
  ./googleearth-bin [0x804c75d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb62c6ea2]
  ./googleearth-bin(__gxx_personality_v0+0x4d) [0x804a981]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/chris/.googleearth/crashlogs/crashlog-F0336368.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions."


Any help ? 

ta

---

### Post by MKR. on 2006-10-17
sudo apt-get install libpng

See if that works (you _appear_ to be missing it).

---

### Post by hvc123 on 2006-10-17
thanks,

it failed 
could not find package

sudo apt-get install libpng
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libpng

---

### Post by MKR. on 2006-10-17
Hmm; I don't know what to tell you. I have it, yet it's not in the repos.

Run: locate libpng

---

### Post by hvc123 on 2006-10-17
ok done that. this is odd because it used to work, obvioulsy uninstalled something 

/var/lib/dpkg/info/libpng12-0.list
/var/lib/dpkg/info/libpng12-0.md5sums
/var/lib/dpkg/info/libpng12-0.postinst
/var/lib/dpkg/info/libpng12-0.postrm
/var/lib/dpkg/info/libpng12-0.shlibs
/home/chris/google-earth/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/VMware-server-linux-client-1.0.0-28343.zip_FILES/VMware-server-console-1.0.0-28343.i386.rpm_FILES/usr/lib/vmware-server-console/lib/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/VMware-server-linux-client-1.0.0-28343.zip_FILES/VMware-server-console-1.0.0-28343.i386.rpm_FILES/usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/VMware-server-linux-client-1.0.0-28343.zip_FILES/vmware-server-console-distrib/lib/lib/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/VMware-server-linux-client-1.0.0-28343.zip_FILES/vmware-server-console-distrib/lib/lib/libpng12.so.0/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/vmware-server-distrib/lib/lib/libpng12.so.0
/mnt/stuff/STUFF/Appz/VmServLinux/vmware-server-distrib/lib/lib/libpng12.so.0/libpng12.so.0
/opt/googleearth/libpng12.so.0
/usr/lib/gthumb/modules/libpngexporter.so
/usr/lib/libpng12.so.0
/usr/lib/libpng12.so.0.1.2.8
/usr/lib/vlc/codec/libpng_plugin.so
/usr/lib/vmware/lib/libpng12.so.0
/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
/usr/lib/vmware-server-console/lib/libpng12.so.0
/usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0
/usr/local/google-earth/libpng12.so.0
/usr/share/doc/libpng12-0
/usr/share/doc/libpng12-0/ANNOUNCE
/usr/share/doc/libpng12-0/KNOWNBUG
/usr/share/doc/libpng12-0/README.Debian
/usr/share/doc/libpng12-0/README.gz
/usr/share/doc/libpng12-0/TODO
/usr/share/doc/libpng12-0/changelog.Debian.gz
/usr/share/doc/libpng12-0/changelog.gz
/usr/share/doc/libpng12-0/copyright

---

### Post by Old Pink on 2006-10-17
Where are you installing from? 

Try getting automatix ([http://www.getautomatix.com](http://www.getautomatix.com)) and installing Google Earth from the list there? 

Personally I've tried both installing from earth.google.com and from automatix, and both worked equally well.

---

### Post by hvc123 on 2006-10-17
ok done that through automatrix.

guess what it works !!! 


nice one

---

### Post by wsetyonugroho on 2006-10-17
i tried to download from automatix.
it said complete .....but, where is my google earth ?
what should i do ?

---

### Post by Benedolt on 2006-12-25
wsetyonugroho, check whether Google Earth is really installed. Run 'locate google-earth'.

hvc123, What version of libpng did you install in order to get Google Earth running again?

---

