---
title: "Having trouble installing lmms"
date: 2013-08-07
forum: General Help
---

### Post by Dadalama on 2013-08-07
```
dadalama@dadalama-System-Product-Name:~$ sudo apt-get install lmms
[sudo] password for dadalama: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  vcf
The following NEW packages will be installed:
  lmms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,042 kB of archives.
After this operation, 9,138 kB of additional disk space will be used.
(Reading database ... 885201 files and directories currently installed.)
Unpacking lmms (from .../lmms_0.4.10-2ubuntu1.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/lmms_0.4.10-2ubuntu1.1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/applications/lmms.desktop', which is also in package lmms-common 0.4.14~rc1-1sound2~12.04
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/lmms_0.4.10-2ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what I'm getting when I try to install lmms using the terminal.

```
/usr/bin/ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/x86_64-linux-gnu/wine/libwinecrt0.a(exe_entry.o)) to format elf32-i386 (RemoteVstPlugin.SIugJt.o) is not supported
winebuild: /usr/bin/ld failed with status 1
winegcc: winebuild failed
make[2]: *** [plugins/vst_base/RemoteVstPlugin] Error 2
make[1]: *** [plugins/vst_base/CMakeFiles/vstbase.dir/all] Error 2
make: *** [all] Error 2
dadalama@dadalama-System-Product-Name:~/Downloads/lmms-0.4.15/build$ 


```
^What I get when I try to compile it from the tar.bz2 file

---

