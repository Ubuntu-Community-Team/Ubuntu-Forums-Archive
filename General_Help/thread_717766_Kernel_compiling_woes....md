---
title: "Kernel compiling woes..."
date: 2008-03-07
forum: General Help
---

### Post by chadjohnson on 2008-03-07
I followed [this]("http://ubuntuforums.org/showthread.php?t=311158") tutorial to compile the 2.6.24.3 kernel, but the computer has all kinds of problems after booting into the new kernel:

[LIST]
[*]I get a splash screen, but after that I just get a blank screen with flashing cursor. I tried installing the ATI fglrx drivers, but this did not fix the problem. If I edit the kernel boot options, I can get to a tty, restart gdm, and login to GNOME. When I do log in to GNOME, Compiz-Fusion does work as normal.
[*]Wireless does not work. The lights on my PCMCIA card do not light up, and the device cannot be found--even after building and installing the madwifi drivers and running 'modprobe ath_pci' (which does load the module), which have worked recently in the past.
[*]eth0 is listed as a device in ifconfig output, but dhclient will not bring it up, even after reboot.
[*]Amazingly after compiling Intel HD as a module, sound does work.
[*]I followed [these]("https://help.ubuntu.com/community/Kernel/Compile#head-4591a640f1ecb03492f49521d7c055cba2845ca1") instructions to compile the restricted modules, but I either get compile errors (see below), or when I compile and install the deb packages, it fixes nothing.
[*]Made a symlink: /lib/2.6.24.3-with-slab -> /lib/firmware/2.6.22-14-generic
[/LIST]

Everyone on that thread says it works for them...but it doesn't work for me. I need to recompile the kernel without SLUB because I am affected by [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/") bug. I've wasted three days trying to get this to work.

This fglrx/kernel incompatibility is present in every single linux distribution I have tried (OpenSUSE, Mandriva, Ubuntu).

Example error from restricted module compiling:
```

dpkg-gencontrol: warning: unknown information field 'L Launchpad-Bugs-Fixed' in input data in parsed version of changelog
Warning: target directory exists .
/usr/src/linux-headers-2.6.24.3-with-slab/arch/x86/Makefile:15: /usr/src/linux-headers-2.6.24.3-with-slab/arch/x86/Makefile_32: No such file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:11,
                 from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:43,
                 from <command line>:1:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/asm/posix_types.h:13:22: error: features.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/asm/posix_types.h:14:35: error: no include path in which to search for asm/posix_types.h
In file included from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:43,
                 from <command line>:1:
include/linux/types.h:12:23: error: asm/types.h: No such file or directory
In file included from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:43,
                 from <command line>:1:
include/linux/types.h:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__kernel_dev_t'
include/linux/types.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'dev_t'
include/linux/types.h:20: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ino_t'
include/linux/types.h:21: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'mode_t'
include/linux/types.h:22: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'nlink_t'
include/linux/types.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'off_t'
include/linux/types.h:24: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'pid_t'
include/linux/types.h:25: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'daddr_t'
include/linux/types.h:27: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'suseconds_t'
include/linux/types.h:28: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'timer_t'
include/linux/types.h:29: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'clockid_t'
include/linux/types.h:35: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uid_t'
include/linux/types.h:36: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gid_t'
include/linux/types.h:37: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uid16_t'
include/linux/types.h:38: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gid16_t'
include/linux/types.h:44: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'old_uid_t'
include/linux/types.h:45: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'old_gid_t'
include/linux/types.h:57: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'loff_t'
include/linux/types.h:66: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'size_t'
include/linux/types.h:71: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ssize_t'
include/linux/types.h:76: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ptrdiff_t'
include/linux/types.h:81: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'time_t'
include/linux/types.h:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'clock_t'
include/linux/types.h:91: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'caddr_t'
include/linux/types.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'u_int8_t'
include/linux/types.h:110: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int8_t'
include/linux/types.h:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'u_int16_t'
include/linux/types.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int16_t'
include/linux/types.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'u_int32_t'
include/linux/types.h:114: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int32_t'
include/linux/types.h:118: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uint8_t'
include/linux/types.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uint16_t'
include/linux/types.h:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uint32_t'
include/linux/types.h:123: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'uint64_t'
include/linux/types.h:124: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'u_int64_t'
include/linux/types.h:125: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int64_t'
include/linux/types.h:140: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sector_t'
include/linux/types.h:180: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__le16'
include/linux/types.h:181: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__be16'
include/linux/types.h:182: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__le32'
include/linux/types.h:183: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__be32'
include/linux/types.h:185: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__le64'
include/linux/types.h:186: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__be64'
include/linux/types.h:188: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__sum16'
include/linux/types.h:189: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__wsum'
include/linux/types.h:197: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'resource_size_t'
include/linux/types.h:203: error: expected specifier-qualifier-list before '__kernel_daddr_t'
In file included from include/linux/kernel.h:11,
                 from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/linkage.h:4:25: error: asm/linkage.h: No such file or directory
In file included from include/linux/kernel.h:15,
                 from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/bitops.h:17:24: error: asm/bitops.h: No such file or directory
In file included from include/linux/kernel.h:15,
                 from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/bitops.h: In function 'get_bitmask_order':
include/linux/bitops.h:29: error: implicit declaration of function 'fls'
include/linux/bitops.h: In function 'hweight_long':
include/linux/bitops.h:45: error: implicit declaration of function 'hweight32'
include/linux/bitops.h:45: error: implicit declaration of function 'hweight64'
include/linux/bitops.h: At top level:
include/linux/bitops.h:53: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'rol32'
include/linux/bitops.h:63: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ror32'
include/linux/bitops.h: In function 'fls_long':
include/linux/bitops.h:72: error: implicit declaration of function 'fls64'
In file included from include/linux/kernel.h:16,
                 from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/log2.h: At top level:
include/linux/log2.h:32: error: expected ')' before 'n'
include/linux/log2.h:40: error: expected ')' before 'n'
In file included from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/kernel.h:17:27: error: asm/byteorder.h: No such file or directory
include/linux/kernel.h:18:21: error: asm/bug.h: No such file or directory
include/linux/kernel.h:47:24: error: asm/div64.h: No such file or directory
In file included from /usr/src/linux-restricted-modules-2.6.24-2.6.24.10.orig/debian/build/2.6.24.3-with-slab/madwifi/ath/../include/compat.h:68,
                 from <command line>:1:
include/linux/kernel.h:148: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:149: error: format string argument not a string type
include/linux/kernel.h:149: warning: conflicting types for built-in function 'snprintf'
include/linux/kernel.h:150: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:151: warning: conflicting types for built-in function 'vsnprintf'
include/linux/kernel.h:152: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:153: error: format string argument not a string type
include/linux/kernel.h:154: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:251: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:253: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:256: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:258: error: expected declaration specifiers or '...' before 'size_t'
include/linux/kernel.h:319:2: error: #error "Please fix asm/byteorder.h"

```

---

### Post by HermanAB on 2008-03-07
I looked at the guide and it looks fine.

However, compiling the kernel for weird hardware can be an adventure.  You should start by first compiling the exact Ubuntu kernel that you originally installed and make sure that it still runs after compiling and installing it.  Only then should you try a different kernel.

Cheers,

Herman

---

### Post by chadjohnson on 2008-03-07
Hey, I got things to compile :) However, it only built the -386, -generic, -rt, and-xen linux-restricted-modules, along with linux-restricted-modules-common, but it did not build -with-slab (my appended version). Any idea why?

Everything seems to work except the wireless. the PCMCIA ath0 does not exist when I run ifconfig. Also, run glxinfo, it says it is using Mesa--even though I, after compiling and rebooting into the new kernel, manually installed the 8.3 ATI drivers. I assume one or both of these issues is due to not having the linux-restricted-modules-2.6.22.9-with-slab modules.

---

### Post by chadjohnson on 2008-03-08
ba bump

I would just like a lead on what is causing eth0 to not come up or what is causing my PCMCIA wireless card to not be recognized.

---

### Post by chadjohnson on 2008-03-08
After manually installing the ATI fglrx driver as well as madwifi and then going to the Restricted Drivers Manager, it says I need to install the package linux-restricted-modules-2.6.22.9-with-slab. The problem is, I cannot build this package as -generic, -rt, -xen, and -386 are the only linux-restricted-modules packages that get built when I compile the linux-restricted-modules.

This sucks. Can someone help please?

---

### Post by Whiffle on 2008-03-08
Which ethernet card are you using?  

I think I would download the madwifi drivers manually and compile them.  Since you compiled a custom kernel, the drivers available through the restricted drivers manager do not apply to you.

---

### Post by chadjohnson on 2008-03-08
That's actually exactly what I had tried. I downloaded them from [here]("http://sourceforge.net/project/showfiles.php?group_id=82936"), ran make, and make install, and rebooted.

The wireless card is a Trendnet TEW-441PC, and the wired ethernet Realtek ([laptop specs]("http://support.acer-euro.com/drivers/notebook/as_5050.html")).

---

### Post by Whiffle on 2008-03-08
After rebooting, do the modules get loaded?  I'm not sure if make install will set it up so that the kernel modules are getting loaded.  You can check with lsmod.  I'm not certain what the names of the madwifi modules, but one of them used to be ath_pci iirc.

---

### Post by chadjohnson on 2008-03-08
Ok, I no longer had the kernel source as I had reverted to an earlier harddrive image, so I just got done rebuilding the kernel.

I have not tried loading the madwifi modules yet--but will soon--but I did notice some very odd output after building the kernel. The same thing as described [here]("http://linux.derkeiler.com/Mailing-Lists/Debian/2006-07/msg00441.html") happened to me. Maybe, just maybe this is why things are not working (could it be?). Should raw bash code be outputted to the console? If not, any idea how to fix this problem?

---

### Post by chadjohnson on 2008-03-09
I know it loaded ath_pci, but I am not sure about others which may also need to have been loaded.

Just now I tried to compile using the newer method described [here]("https://help.ubuntu.com/community/Kernel/Compile#head-8c49b0182e468c06a768e6abb2f2ff343a9158a9").  It compiled fine; however, when I install the deb package my original kernel gets overwritten! What the crap? I assume a way around this is to specify a different version name for the kernel, either by modifying some debian/* files or by adding something to the command
```

AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-FLAVOUR

```

Any clues? I've search extensively but have found nothing.

---

### Post by chadjohnson on 2008-03-09
Well, I finally managed to build the linux-restricted-modules for the kernel which I built, I installed them, and then tried to modprobe ath_pci, but it said "hardware doesn't respond as expected." I then built the madwifi driver modules located in the linux-restricted-modules source dir, applying the patches provided. They built and installed fine, so I modprobed all the original modules, and a) the pcmcia card's lights do not come on, and b) ifconfig says the device does not exist! eth0 still does not come up, though it is recognized.

!@#$%^&!!!!!!!!

Very soon I am going to say screw Ubuntu altogether and go back to Windows XP. It should not be this hard...WTF am I doing wrong???

(I'm sorry, I am not aiming that at you in any way. I have been at this for *4* days though, and I have gotten absolutely nowhere whatsoever)

---

### Post by geraldm on 2008-03-09
The kernel being compiled will not overwrite a kernel WHEN THE KERNEL SOURCE is compiled with a different suffix char.  Note that this will affect the value returned by "uname -r" command.
This option is in the KERNELTOPSOURCE/.config file, at the beginning, under "General setup" heading.

CONFIG_LOCALVERSION="n"

Gerald

---

### Post by chadjohnson on 2008-03-09
I assume this is an alternative to the make-kpkg option --append-to-version? How do I do this when running the command
```

AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-FLAVOUR

```
? I modified CONFIG_LOCALVERSION in debian/config/i386/config, and it still overwrites my original kernel...

*EDIT* Let me add, when I run
```

make-kpkg --initrd --append-to-version=-generic kernel_image kernel_headers modules_image

```
Using the apt package linux-source-2.6.22, the kernel package is named with a ".9" at the end, like linux-image-2.6.22.9-generic....deb. Where does this ".9" come from?

*EDIT2* Nevermind, ".9" is in EXTRAVERSION in Makefile.

---

### Post by chadjohnson on 2008-03-11
Well, I tried downgrading to the Feisty kernel again, and this time it worked...I don't know what happened before. I still need to test things.

For now, I'll just use my desktop which has an nVidia card.

---

