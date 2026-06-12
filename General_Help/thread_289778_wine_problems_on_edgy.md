---
title: "wine problems on edgy"
date: 2006-10-31
forum: General Help
---

### Post by tempo500 on 2006-10-31
hi,

its impossible to install wine on edgy for me! i get this error no mather what.

```
bhil@workstation:~/src/wine-0.9.24$ winecfg
wine: creating configuration directory '/home/bhil/.wine'...
wine: Unhandled page fault on read access to 0x003c0023 at address 0x7ef9aea9 (thread 0009), starting debugger...
wine: Unhandled page fault on read access to 0x003c001b at address 0x7ef9aea9 (thread 000b), starting debugger...
wine: Unhandled page fault on read access to 0x003c0013 at address 0x7ef9aea9 (thread 000d), starting debugger...
err:ntdll:RtlpWaitForCriticalSection section 0x7e9802c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0009, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e97e2c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000d, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e97e2c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000b, blocked by 0000, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0x7ef9a88a

```

its always the same error i installed wine from the original ubuntu repository - from [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) (0.9.24)
i compiled 0.9.22, 23, 24
with those packages installed - [winhq]("http://wiki.winehq.org/Recommended_Packages")
```
./configure CFLAGS=-fno-stack-protector
make depend
make
sudo make install
```

it compiles fine, just starting winecfg gives me the error.

---

### Post by dantum on 2006-11-01
Hi,

I am not getting this error yet. Instead i get this when i do "./configure CFLAGS=-fno-stack-protector"

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL development headers were found
stead i get this 

How did you manage to get past that?

---

### Post by tempo500 on 2006-11-01
i am really no linux guru... but i read somewhere that you need to have the official graphics drivers installed, frglx, nvidia. check the winhq recommend packages... link is above. i am just a trial and error, howto, tutorial guy, so i dont know much of the internals of linux, but it sounds like you are missing some source packages. phil

---

### Post by reiki on 2006-11-01
I'm working on this myself and I will relate a few things..

#1 make sure you uninstall a previous version of wine before installing a newly compiled one.

#2 Using the winhq sources try compiling with:
./configure CFLAGS="-fno-stack-protector -O2"

#3 Before you install your newly compiled Wine version, rename your .wine directory. Do this so that your new Wine can create the directory fresh. Do this by running winecfg after you install the newly compiled Wine. I suspect that when we recompile Wine and try to use an existing .wine directory we may be introducing some mismatched libraries. I'm not SURE of this, but it's what I'll be doing. Pretty easy to either reinstall a program into Wine or rsync the specific program directory (ONLY the Program File/your_specific_program directory... nothing else) over into the new .wine directory.

I won't switch to Edgy until I can reliably run World of Warcraft in Wine. So I'm working on this one as much as time allows me to and reading everything on appdb.winhq ( [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) )

---

### Post by tempo500 on 2006-11-02
hi,

thanx for your input! sadly it did not work for me.
i uninstall the sources with sudo make uninstall and make clean.

i compiled the 0.9.22 and 0.9.24 with ./configure CFLAGS="-fno-stack-protector -O2"

i deleted my aborted wine.balaba directories

wincfg still fails with the same message. i am starting to think that its not wine... i read something about issues with fire-gl graphic cards, though this message went back to wine version .9.12...so.... meanwhile i got frustrated and found out that there exists something called kreta... a native linux paint program!!! its not really for gnome but better than running corel painter through wine... i guess. but i would still like to know how i can run wine on my workstation! any help apretiated. phil

---

### Post by khermans on 2006-11-04
sudo aptitude install xlibmesa-gl-dev

---

### Post by tempo500 on 2006-11-04
i upgraded the ati drivers to 8.30.3. so i deinstalled the old ati drivers and tried wine 9.24, which works!! with the native ubuntu ati drivers. after a restart with the new ati drivers - and starting winecfg gives me this... maybe someone can "debug" this for me?

```
bhil@workstation:~/.wine/drive_c/Program Files/Painter9$ winecfg
wine: Unhandled page fault on read access to 0x003c0023 at address 0x7bc27b05 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x003c0023 in 32-bit code (0x7bc27b05).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:ffff GS:0033
 EIP:7bc27b05 ESP:0033ede0 EBP:0033edf8 EFLAGS:00210257(   - 00     RIZAP1C)
 EAX:003bffff EBX:7bc76940 ECX:7e689364 EDX:7e689364
 ESI:7e689360 EDI:00000000
Stack dump:
0x0033ede0:  7e50b979 7e67da8f 00000050 7e68671c
0x0033edf0:  00000000 00000000 0033ee08 7e661e30
0x0033ee00:  7e689360 7e68671c 0033ee48 7e64e847
0x0033ee10:  7e67da8f 7e67d88b 00000000 00000000
0x0033ee20:  00000004 081c153c b7dd1158 00000000
0x0033ee30:  00000020 b7dd1130 7ffdf044 7e68671c
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7bc27b05 RtlEnterCriticalSection+0x35 in ntdll (0x0033edf8)
  2 0x7e661e30 wine_tsx11_lock+0x20 in winex11 (0x0033ee08)
  3 0x7e64e847 in winex11 (+0x3e847) (0x0033ee48)
  4 0x7e64ec56 X11DRV_setup_opengl_visual+0x66 in winex11 (0x0033eed8)
  5 0x7e6633fa in winex11 (+0x533fa) (0x0033f028)
  6 0x7e673453 in winex11 (+0x63453) (0x0033f048)
  7 0x7bc36705 call_dll_entry_point+0x15 in ntdll (0x0033f068)
  8 0x7bc377ac in ntdll (+0x277ac) (0x0033f118)
  9 0x7bc37c4d in ntdll (+0x27c4d) (0x0033f158)
  10 0x7bc39db7 LdrLoadDll+0x87 in ntdll (0x0033f188)
  11 0x7b860bcb in kernel32 (+0x40bcb) (0x0033f3d8)
  12 0x7b860de0 LoadLibraryExW+0x50 in kernel32 (0x0033f408)
  13 0x7b860f03 LoadLibraryExA+0x43 in kernel32 (0x0033f428)
  14 0x7b860f3d LoadLibraryA+0x2d in kernel32 (0x0033f448)
  15 0x7eab27f0 DRIVER_load_driver+0x1c0 in gdi32 (0x0033f5b8)
  16 0x7eaae540 CreateDCW+0x60 in gdi32 (0x0033f868)
  17 0x7eb77c70 CreateIconFromResourceEx+0x420 in user32 (0x0033f908)
  18 0x7eb78607 in user32 (+0x28607) (0x0033f968)
  19 0x7eb78b4b LoadImageW+0x3fb in user32 (0x0033fa08)
  20 0x7eb79236 LoadImageA+0x56 in user32 (0x0033fae8)
  21 0x7eb794d4 LoadCursorA+0x44 in user32 (0x0033fb18)
  22 0x7eb6f1ef in user32 (+0x1f1ef) (0x0033fb38)
  23 0x7eb6f23d CLASS_RegisterBuiltinClasses+0x1d in user32 (0x0033fb48)
  24 0x7ebe2bd2 in user32 (+0x92bd2) (0x0033fbc8)
  25 0x7ebf5913 in user32 (+0xa5913) (0x0033fbe8)
  26 0x7bc36705 call_dll_entry_point+0x15 in ntdll (0x0033fc08)
  27 0x7bc377ac in ntdll (+0x277ac) (0x0033fcb8)
  28 0x7bc37c4d in ntdll (+0x27c4d) (0x0033fcf8)
  29 0x7bc37b92 in ntdll (+0x27b92) (0x0033fd38)
  30 0x7bc37b92 in ntdll (+0x27b92) (0x0033fd78)
  31 0x7bc37b92 in ntdll (+0x27b92) (0x0033fdb8)
  32 0x7bc37b92 in ntdll (+0x27b92) (0x0033fdf8)
  33 0x7bc37b92 in ntdll (+0x27b92) (0x0033fe38)
  34 0x7bc3aa61 LdrInitializeThunk+0x371 in ntdll (0x0033ff08)
  35 0x7b86f4aa in kernel32 (+0x4f4aa) (0x0033ffe8)
  36 0xb7e00567 wine_switch_to_stack+0x17 in libwine.so.1 (0x00000000)
0x7bc27b05 RtlEnterCriticalSection+0x35 in ntdll: movl  0x24(%eax),%eax
Modules:
Module  Address                 Debug info      Name (61 modules)
ELF     7b800000-7b91a000       Export          kernel32<elf>
  \-PE  7b820000-7b91a000       \               kernel32
ELF     7bc00000-7bc81000       Export          ntdll<elf>
  \-PE  7bc10000-7bc81000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dabd000-7dac6000       Deferred        librt.so.1
ELF     7db92000-7e474000       Deferred        fglrx_dri.so
ELF     7e474000-7e514000       Deferred        libgl.so.1
ELF     7e514000-7e5dd000       Deferred        libx11.so.6
ELF     7e5dd000-7e5ea000       Deferred        libxext.so.6
ELF     7e5ea000-7e602000       Deferred        libice.so.6
ELF     7e602000-7e68f000       Export          winex11<elf>
  \-PE  7e610000-7e68f000       \               winex11
ELF     7e68f000-7e6ad000       Deferred        libexpat.so.1
ELF     7e6ad000-7e6dc000       Deferred        libfontconfig.so.1
ELF     7e6dc000-7e6f0000       Deferred        libz.so.1
ELF     7e6f0000-7e75a000       Deferred        libfreetype.so.6
ELF     7e75a000-7e78c000       Deferred        uxtheme<elf>
  \-PE  7e760000-7e78c000       \               uxtheme
ELF     7e78c000-7e815000       Deferred        winmm<elf>
  \-PE  7e7a0000-7e815000       \               winmm
ELF     7e815000-7e845000       Deferred        winspool<elf>
  \-PE  7e820000-7e845000       \               winspool
ELF     7e845000-7e905000       Deferred        comctl32<elf>
  \-PE  7e850000-7e905000       \               comctl32
ELF     7e905000-7e918000       Deferred        libresolv.so.2
ELF     7e91c000-7e921000       Deferred        libxdmcp.so.6
ELF     7e921000-7e92a000       Deferred        libsm.so.6
ELF     7e92a000-7e948000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e948000       \               iphlpapi
ELF     7e948000-7e99a000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e99a000       \               rpcrt4
ELF     7ea79000-7eb2f000       Export          gdi32<elf>
  \-PE  7ea90000-7eb2f000       \               gdi32
ELF     7eb2f000-7ec65000       Export          user32<elf>
  \-PE  7eb50000-7ec65000       \               user32
ELF     7ec65000-7ecab000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecab000       \               advapi32
ELF     7ecab000-7ed3f000       Deferred        ole32<elf>
  \-PE  7ecc0000-7ed3f000       \               ole32
ELF     7ed3f000-7ed97000       Deferred        shlwapi<elf>
  \-PE  7ed50000-7ed97000       \               shlwapi
ELF     7ed97000-7ee81000       Deferred        shell32<elf>
  \-PE  7edb0000-7ee81000       \               shell32
ELF     7ee81000-7ef1d000       Deferred        comdlg32<elf>
  \-PE  7ee90000-7ef1d000       \               comdlg32
ELF     7ef1d000-7ef74000       Deferred        winecfg<elf>
  \-PE  7ef20000-7ef74000       \               winecfg
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efee000       Deferred        libm.so.6
ELF     7efee000-7eff1000       Deferred        libxau.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c92000-b7c9b000       Deferred        libnss_compat.so.2
ELF     b7c9c000-b7ca0000       Deferred        libdl.so.2
ELF     b7ca0000-b7dd4000       Deferred        libc.so.6
ELF     b7dd4000-b7de7000       Deferred        libpthread.so.0
ELF     b7de7000-b7df2000       Deferred        libgcc_s.so.1
ELF     b7df9000-b7f0a000       Export          libwine.so.1
ELF     b7f0c000-b7f27000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==

```

---

### Post by zek725 on 2006-11-04
> **tempo500 said:**
> i am really no linux guru... but i read somewhere that you need to have the official graphics drivers installed, frglx, nvidia. check the winhq recommend packages... link is above. i am just a trial and error, howto, tutorial guy, so i dont know much of the internals of linux, but it sounds like you are missing some source packages. phil

I've installed Wine from the official Edgy repository.

```
sudo aptitude install wine
```

Installation went fine. However, clicking the AUDIO tab in winecfg returns this error.

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/zek/.kde/socket-warrior2.
can't create mcop directory
```

Edit:
> **Eliseo said:**
> Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing!

IT WORKED! No longer crashes but terminal outputs these lines:

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: not found
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

**winecfg** tells me that there are no audio drivers installed/found in registry. It chose for me OSS. I think ALSA is more stable?

---

### Post by tempo500 on 2006-11-05
great! ;) i solved my painting needs with gimp!!the brush creator is more powerful than i thought... - wine? well...

```
bhil@workstation:~$ wine --version
Wine 0.9.22
bhil@workstation:~$ winecfg
wine: Unhandled page fault on read access to 0x003c0023 at address 0x7efa7b25 (thread 0009), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) (null)
        00000009    0

```

---

### Post by duckinatux on 2007-08-08
I installed Wine 0.9.9 using the add/remove applications function (advanced options), and while everything works fine so far, i can't get any audio, and if i even TRY to open the "audio" tab in winecfg it brings up this:
```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c07c0b8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
```
and then winecfg freezes.

i'm running a realtek HD audio onboard soundchip, if that makes any difference, and i'm extremely new to linux, so most linux terminology goes over my head, hence why most anything i can find via google doesn't help me one bit. i've tried looking for some kind of package which will write the necessary drivers to the directory "/dev/snd/" but to no avail.

also, based on the searches I've done, it looks like nobody really knows how to fix this problem...

---

