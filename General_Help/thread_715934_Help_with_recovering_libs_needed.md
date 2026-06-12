---
title: "Help with recovering libs needed"
date: 2008-03-05
forum: General Help
---

### Post by yaroslavtsev on 2008-03-05
After I have pressed "Reset" at some unfortunate moment some of the important library files are broken in my Ubuntu, these include libattr.so.1.1.0, libmemusage.so, libcrypt-2.6.1.so and some others (about 10 libraries overall). The console still works, but with some limitations (ls crashes, apt-get works badly). How can I recover the libraries?

---

### Post by kellemes on 2008-03-05
Can you please be more specific about your issues?
At what point is ls crashing?
Why is apt-get working badly? What's happening?

---

### Post by yaroslavtsev on 2008-03-05
when loading ubuntu I get the following errors:
*Configuring network interfaces...
/etc/ppp/ip-down.d/0dns-down: 49: awk: Input/output error
mv:  error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error
mv:  error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error
mv:  error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error
mv:  error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error
mv:  error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error
*Saving VESA state...
/etc/rc2.dS10acpid: 98: awk: Input/output error
*Doing Wacom setup...
*(red color) Can't start Hardware abstraction layer - please ensure dbus is running
+ some more errors

when I login into terminal I've got a bunch of messages:
-bash: /dev/null: Permission denied

ls outputs the following:
ls: error while loading shared libraries: libattr.so.1: cannot open shared object file: Input/output error

---

### Post by pointone on 2008-03-05
You should probably run a fsck on your root partition.

```
sudo touch /forcefsck
```

... and reboot the computer to have it scan.

---

