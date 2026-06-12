---
title: "KMOD crashes on startup"
date: 2018-01-11
forum: General Help
---

### Post by michael337 on 2018-01-11
This happened this morning when I turned on my computer. I can't tell if this is a meltdown problem, but now I'm afraid to reboot my system. This problem started when I autoremoved two older versions of the kernel, but dpkg said that some packages has their files list file missing and that it assumes that they aren't installed.
```
dpkg: warning: files list file for package 'libnm-gtk-common' missing; assuming package has no files currently installeddpkg: warning: files list file for package 'libsoup-gnome2.4-1:i386' missing; assuming package has no files currently installeddpkg: warning: files list file for package 'doc-base' missing; assuming package has no files currently installeddpkg: warning: files list file for package 'libpython2.7-dev:amd64' missing; assuming package has no files currently installeddpkg: warning: files list file for package 'libraw1394-doc' missing; assuming package has no files currently installeddpkg: warning: files list file for package 'gnome-session-common' missing; assuming package has no files currently installed
``` 
Then I rebooted the computer, so that the error would disappear, but it didn't.
When I turned on my computer, apport opens, saying that a system problem has been detected. I clicked report problem. Another window opens, apologizing that ubuntu 16.04 has experienced an error. After a while, I put my computer on standby. In the afternoon I started backing up my home folder into an external drive. 
here is the apport log:
```
ERROR: apport (pid 8676) Thu Jan 11 09:30:17 2018: called for pid 8675, signal 7, core limit 0, dump mode 1
ERROR: apport (pid 8676) Thu Jan 11 09:30:17 2018: executable: /bin/kmod (command line "depmod -a -F /boot/System.map-4.4.0-98-generic 4.4.0-98-generic")
ERROR: apport (pid 8676) Thu Jan 11 09:30:17 2018: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 8676) Thu Jan 11 09:30:18 2018: wrote report /var/crash/_bin_kmod.0.crash

```
Shortly after, I updated my repositories a couple of times. Since I'm using an 1st gen intel i5 processor, an upgrade package appeared for intel-microcode, in the afternoon. I installed it, and nothing happened. Should I be concerned about the current installation of ubuntu 16.04, right now?

---

### Post by michael337 on 2018-01-12
Bump

---

