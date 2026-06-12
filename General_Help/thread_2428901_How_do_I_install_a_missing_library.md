---
title: "How do I install a missing library?"
date: 2019-10-10
forum: General Help
---

### Post by Jorhel on 2019-10-10
Hi 
I have installed Lutris in order to play the game Papers, Please, downloaded from GOG.
When I press play nothing happen, the log says:


 ./PapersPlease: error while loading shared libraries: libstdc++.so.6:
 wrong ELF class: ELFCLASS64 Waiting on children Exit with returncode
 127


How do I install the missing library please?

---

### Post by Dennis N on 2019-10-11
The Description on GOG says it's a 32-bit game. You need 32-bit library libx32stdc++6:i386

Use terminal:
```
sudo apt install libx32stdc++6:i386
```

Did you look at the System Requirements > Other? It lists several needed 32-bit libraries. If you don't have all of those installed, you will get errors.

---

### Post by Jorhel on 2019-10-11
Thanks yes I looked at it but since I wasn't sure where to look for them I thought I'll give it a shot.
I installed it now but the game still don't find it. I read somewhere else that the lib 64 is before the 32 so it does not find it.
Could that be it?

---

### Post by Dennis N on 2019-10-11
Also be sure you have installed these packages: 
```
lib32z1
libc6:i386
libc6-i386

```
Note: lib32z1 is the 32-bit runtime environment. Otherwise 32-bit software won't run.

> I read somewhere else that the lib 64 is before the 32 so it does not find it. Could that be it?
 I don't think so.

---

### Post by Jorhel on 2019-10-11
Hi,
I installed all the missing lib packages but still get the same message in the log when I try to play the game.
I found [here]("https://askubuntu.com/questions/502728/libomniorb4-so-1-wrong-elf-class-elfclass64") something that seem related but when I try the how to fix it nothing happen.
> [COLOR=#242729][FONT=Arial]Looks like your application is a 32 bits application but is trying to load a 64bits library. On a 64bits installation, you can have both version (32 bits and 64 bits) of any libraries installed. 32bits can be found under /usr/lib32 and 64bits under /usr/lib64.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On Linux, libraries are search using a path sequence, a little bit like the PATH variable list all the directories to look for the executable you want to run when no path is given. This sequence to search for libraries is defined in a variable called LD_LIBRARY_PATH.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem is that the directory for the 64bits versions comes before the directory with the 32bits versions. And usually the name of the library is identical for the 32bits and 64bits version.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]You can overcome this problem by creating a small startup script for your application like this one :[/FONT][/COLOR]
#!/bin/bash

export LD_LIBRARY_PATH=/usr/lib32:/usr/lib64:$LD_LIBRARY_PATH

<your binary> $*
[COLOR=#242729][FONT=Arial]If there is already a script to start this application, you can just add the line[/FONT][/COLOR]
export LD_LIBRARY_PATH=/usr/lib32:/usr/lib64:$LD_LIBRARY_PATH
[COLOR=#242729][FONT=Arial]to it, near the top.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'll prefer the first method, creating a specific script, as any startup script provided by the package will be probably overwritten in case of update.[/FONT][/COLOR]

I assume I have to insert those lines of code somewhere specific instead of just running them in the terminal?
And if yes where?
Also I have had a look at  what's in the libraries
> /libx32$ ls 
ld-2.27.so               libmemusage.so         libnss_nisplus-2.27.so
ld-linux-x32.so.2        libm.so.6              libnss_nisplus.so.2
libanl-2.27.so           libmvec-2.27.so        libnss_nis.so.2
libanl.so.1              libmvec.so.1           libpcprofile.so
libBrokenLocale-2.27.so  libnsl-2.27.so         libpthread-2.27.so
libBrokenLocale.so.1     libnsl.so.1            libpthread.so.0
libc-2.27.so             libnss_compat-2.27.so  libresolv-2.27.so
libcidn-2.27.so          libnss_compat.so.2     libresolv.so.2
libcidn.so.1             libnss_dns-2.27.so     librt-2.27.so
libcrypt-2.27.so         libnss_dns.so.2        librt.so.1
libcrypt.so.1            libnss_files-2.27.so   libSegFault.so
libc.so.6                libnss_files.so.2      libthread_db-1.0.so
libdl-2.27.so            libnss_hesiod-2.27.so  libthread_db.so.1
libdl.so.2               libnss_hesiod.so.2     libutil-2.27.so
libm-2.27.so             libnss_nis-2.27.so     libutil.so.1



> /lib64$ ls
ld-linux-x86-64.so.2



> /lib$ ls
apparmor        ifupdown                              netplanbrltty          init                                  recovery-mode
console-setup   klibc-wBFLvVtxy4xJqEadIBJMa78iJz8.so  systemd
cpp             ld-linux.so.2                         terminfo
crda            linux-sound-base                      udev
firmware        lsb                                   ufw
hdparm          modprobe.d                            x86_64-linux-gnu
i386-linux-gnu  modules



I'm I still missing a library somewhere or is it in the wrong directory?

---

### Post by Dennis N on 2019-10-11
On Ubuntu 18.04 where I have my 32-bit games installed, the location of that 32 bit file is: **/usr/lib32/libstdc++.so.6** and the 64-bit file is in **/usr/lib/x86_64-linux-gnu/libstdc++.so.6** and there is no /usr/lib64 directory. 

And I see that many 32-bit libraries ended up in /usr/lib/i386-linux-gnu/ when installed.

I also tried to examine LD_LIBRARY_PATH and found it contains nothing on my sistem; **echo $LD_LIBRARY_PATH** should output a value - presumably some set of folders. I wonder if it's actually used by the system any longer? I don't know.

I've never encountered this kind of problem myself - don't have a good answer for you.

---

### Post by Dennis N on 2019-10-12
I do have a solution after a bit of thought - dual boot your present OS and Ubuntu 16.04 32-bit OS, which is still available for installation and supported, and install your game on that. That won't have any 64-bit libraries to confuse your game software. (If your computer is UEFI, then you can use a virtual machine for the 32-bit system).

---

### Post by Jorhel on 2019-10-13
OK after more research I installed the libraries recommended [here]("https://support.gog.com/hc/en-us/articles/213039665")
and tried starting it from the terminal I now get > ~/Games/papers-please$ ./start.shRunning Papers, Please
Error : Null Function Pointer
Also Got the same from lutris.

---

### Post by mc4man on 2019-10-14
See
[http://papersplea.se/support/?p=32](http://papersplea.se/support/?p=32)
Scroll down to linux section on mesa

If using nvidia drivers **also** see
[https://forums.linuxmint.com/viewtopic.php?t=182645](https://forums.linuxmint.com/viewtopic.php?t=182645)

---

