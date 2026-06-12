---
title: "-bash: ./adb: cannot execute binary file: Exec format error"
date: 2022-07-16
forum: General Help
---

### Post by chat-4432 on 2022-07-16
i try to run [COLOR=#666666][FONT=monospace]./adb devices [/FONT][/COLOR][https://www.xda-developers.com/install-adb-windows-macos-linux/](https://www.xda-developers.com/install-adb-windows-macos-linux/)[COLOR=#666666][FONT=monospace]
it not show [/FONT][/COLOR]prompt 
> [COLOR=#666666][FONT=monospace]Allow USB debugging?[/FONT][/COLOR][COLOR=#666666][FONT=monospace] 
but it show 
[/FONT][/COLOR]```
-bash: ./adb: cannot execute binary file: Exec format error
```[COLOR=#666666][FONT=monospace]
what should i do ??


[/FONT][/COLOR]

---

### Post by TheFu on 2022-07-16
That usually means that a compiled program was compiled for a different platform than the one where it is trying to run.

Check with these commands:
```
$ file /usr/bin/adb
/usr/bin/adb: symbolic link to ../lib/android-sdk/platform-tools/adb

$ file /usr/lib/android-sdk/platform-tools/adb 
/usr/lib/android-sdk/platform-tools/adb: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=fd42260a77da8dafc39448aee8547e3fb70fd6e8, stripped

```
The first command isn't where the real program is, but tells us where.
The 2nd command is with that symbolic link.  It is an x86-64 binary in ELF format and dependent on a shared library, ld-linux-x86-64.

```
$ adb version
Android Debug Bridge version 1.0.39
Version 1:8.1.0+r23-5~18.04
Installed as /usr/lib/android-sdk/platform-tools/adb
```
Happens to work because my abd binary is compatible with the platform.  If I copied this file to an ARM CPU, it won't work.  Or if I copy the ARM compiled version to x86, it won't work there either.

If you think the versions of the platform and the binary match, then you could try doing a *--reinstall* of the program. This can fix corrupted files, but the underlying issue isn't addressed.  These binaries should be gpg signed and only those compatible with the platform should be installed, unless you did something odd or there are hardware errors happening.  Then those issues are all on you.

---

### Post by chat-4432 on 2022-07-17
i change to install using command 
[COLOR=#000000][FONT=monospace]sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000088][FONT=monospace]get[/FONT][/COLOR][COLOR=#000000][FONT=monospace] install android[/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]tools[/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]adb[/FONT][/COLOR]
my first command show like this 
> adb: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.24, not stripped
my 2nd command show 
> Android Debug Bridge version 1.0.41
Version 28.0.2-debian
Installed as /usr/lib/android-sdk/platform-tools/adb

i think i install wrong version
do you know how to uninstall this ??

---

### Post by TheFu on 2022-07-17
> **chat-4432 said:**
>  
do you know how to uninstall this ??

That looks like an ARM binary. Are you one an ARM-64 CPU?

The way to uninstall anything depends on how it was installed in the first place.  Use the uninstall method that matches the install method used.

---

### Post by chat-4432 on 2022-07-17
yes im on ARM-64 CPU.
idk why it not show my devices
$ adb devices
> * daemon not running; starting now at tcp:5037
* daemon started successfully
List of devices attached

---

### Post by TheFu on 2022-07-18
If you are on ARM, you'll get better answers if you clearly say that in the title and in the first paragraph.  Some things are very different on ARM than on x86.
I wouldn't dream of making suggestions for ARM running Ubuntu. Not my skillset, sorry.

---

