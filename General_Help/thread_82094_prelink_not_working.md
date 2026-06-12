---
title: "prelink not working"
date: 2005-10-25
forum: General Help
---

### Post by ubunturulz11 on 2005-10-25
Hi I'm running Ubuntu 5.10 Breezy on a 
AMD Athlon64 3500+ with 512MB RAM 
I tried prelinking and nothing seemed to improve so I looked in my /var/log/prelink file and I had a bunch of errors

usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/libgtkembedmoz.so: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/games/glest/glest.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/firefox-bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/regchrome: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/xpcshell: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/openoffice/program/pkgchk.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/openoffice/program/pluginapp.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: 

/usr/sbin/prelink.bin: /usr/lib/evolution/2.4/evolution-alarm-notify: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/bin/gnome-background-properties: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/gnome-netstatus/gnome-netstatus-applet: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/gnome-applets/trashapplet: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/xscreensaver/pulsar: Cannot prelink against non-PIC shared library /usr/lib/libGL.so.

---

### Post by orbinick on 2005-10-25
did you install from automatix?

did you let it run undisturbed when you installed it?

when you install it there is a lot of disk activity, if it gets interrupted, that will happen.

---

### Post by ubunturulz11 on 2005-10-26
I didn't install it form automatix I installed it from stantard apt-get

I let it run undisturbed. I was logged out of gnome while it was running

---

### Post by mlomker on 2005-10-26
Some of those errors are 'normal'.  I really don't see much of a performance difference with or without it.  I guess people that run OpenOffice can really tell the difference, but I use Koffice, so...

---

### Post by kittcankitt on 2005-11-02
[QUOTE=ubunturulz11]Hi I'm running Ubuntu 5.10 Breezy on a 
AMD Athlon64 3500+ with 512MB RAM 
I tried prelinking and nothing seemed to improve so I looked in my /var/log/prelink file and I had a bunch of errors

usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/libgtkembedmoz.so: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/games/glest/glest.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/firefox-bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/regchrome: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/mozilla-firefox/xpcshell: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/openoffice/program/pkgchk.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: /usr/lib/openoffice/program/pluginapp.bin: Could not find one of the dependencies
/usr/sbin/prelink.bin: 

/usr/sbin/prelink.bin: /usr/lib/evolution/2.4/evolution-alarm-notify: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/bin/gnome-background-properties: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/gnome-netstatus/gnome-netstatus-applet: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/gnome-applets/trashapplet: Cannot prelink against non-PIC shared library /usr/lib/libaudiofile.so.0
/usr/sbin/prelink.bin: /usr/lib/xscreensaver/pulsar: Cannot prelink against non-PIC shared library /usr/lib/libGL.so.[/QUOTE]


I got most of these same errors and my system still seems stable enough.  Would be nice to know why or what went wrong though.  Has anyone shed any insight on this subject?

---

