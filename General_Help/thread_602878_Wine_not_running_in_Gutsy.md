---
title: "Wine not running in Gutsy"
date: 2007-11-04
forum: General Help
---

### Post by cegpope on 2007-11-04
Problem: If I go to Applications -> Wine and click "Configure Wine" nothing seems to happen. Similarly if I attempt to "Browse C:\ Drive" or try to right click on a Windows application and select "Open with Wine Windows Emulator" nothing happens.


I have tried uninstalling and reinstalling wine through: Add/Remove Applications, Synaptic Package Manager, and through Terminal with various commands. Between uninstalling and reinstalling I reboot, I also reboot after each attempt at installing. Nothing changes.


When I run "winecfg" from Terminal this is what I get:
> wine: creating configuration directory '/home/name/.wine'...
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: ]Unhandled page fault on read access to 0x000000b8 at address 0x7e6af889 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e6af889).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e6af889 ESP:0033ee10 EBP:0033ee38 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7c0396f8 EDX:00000000
 ESI:00000000 EDI:7c0462f0
Stack dump:
0x0033ee10:  0003fff4 00000000 0000004c 7ea06b2c
0x0033ee20:  7c0462f0 7c01a238 00000000 00000000
0x0033ee30:  7c0462f0 7c04d8b0 0033ee68 7e8b6705
0x0033ee40:  7c0462f0 00000000 00000000 00000000
0x0033ee50:  7c04d960 00000190 7c0396f8 7ead7c94
0x0033ee60:  00000033 00000000 0033ee98 7e8b597e
Backtrace:
=>1 0x7e6af889 in r300_dri.so (+0x56889) (0x0033ee38)
  2 0x7e8b6705 CreateContext+0xd5() in libgl.so.1 (0x0033ee68)
  3 0x7e8b597e glXCreateContext+0x3e() in libgl.so.1 (0x0033ee98)
  4 0x7ea9e4d7 in winex11 (+0x3e4d7) (0x0033ef18)
  5 0x7ea9ef60 X11DRV_setup_opengl_visual+0x130() in winex11 (0x0033eff8)
  6 0x7eab2f24 in winex11 (+0x52f24) (0x0033f158)
  7 0x7eac4073 in winex11 (+0x64073) (0x0033f178)
  8 0x7bc42225 call_dll_entry_point+0x15() in ntdll (0x0033f198)
  9 0x7bc43bfd in ntdll (+0x33bfd) (0x0033f228)
  10 0x7bc44254 in ntdll (+0x34254) (0x0033f278)
  11 0x7bc46007 LdrLoadDll+0x87() in ntdll (0x0033f2a8)
  12 0x7b8660c0 in kernel32 (+0x460c0) (0x0033f508)
  13 0x7b8662d0 LoadLibraryExW+0x50() in kernel32 (0x0033f538)
  14 0x7b8663f3 LoadLibraryExA+0x43() in kernel32 (0x0033f558)
  15 0x7b86642d LoadLibraryA+0x2d() in kernel32 (0x0033f578)
  16 0x7ecd1054 DRIVER_load_driver+0x1e4() in gdi32 (0x0033f6f8)
  17 0x7eccb620 CreateDCW+0x60() in gdi32 (0x0033f9a8)
  18 0x7ed7e030 CreateIconFromResourceEx+0x420() in user32 (0x0033fa48)
  19 0x7ed7ea47 in user32 (+0x2ea47) (0x0033fac8)
  20 0x7ed7fceb LoadImageW+0x3fb() in user32 (0x0033fb68)
  21 0x7ed80286 LoadImageA+0x56() in user32 (0x0033fc48)
  22 0x7ed80777 LoadCursorA+0x97() in user32 (0x0033fc78)
  23 0x7ed754ff in user32 (+0x254ff) (0x0033fc98)
  24 0x7ed7554d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0033fcb8)
  25 0x7edeb6e2 in user32 (+0x9b6e2) (0x0033fd38)
  26 0x7ee00183 in user32 (+0xb0183) (0x0033fd58)
  27 0x7bc42225 call_dll_entry_point+0x15() in ntdll (0x0033fd78)
  28 0x7bc43bfd in ntdll (+0x33bfd) (0x0033fe08)
  29 0x7bc44254 in ntdll (+0x34254) (0x0033fe58)
  30 0x7bc44182 in ntdll (+0x34182) (0x0033fea8)
  31 0x7bc46d06 LdrInitializeThunk+0x2b6() in ntdll (0x0033ff08)
  32 0x7b874f2a in kernel32 (+0x54f2a) (0x0033ffe8)
  33 0xb7ece9d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e6af889: movl        0xb8(%esi),%eax
Modules:
Module  Address                 Debug info      Name (39 modules)
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e64f000-7e659000       Deferred        libdrm.so.2
ELF     7e659000-7e88a000       Export          r300_dri.so
ELF     7e88a000-7e914000       Export          libgl.so.1
ELF     7e914000-7e919000       Deferred        libxdmcp.so.6
ELF     7e919000-7ea0a000       Deferred        libx11.so.6
ELF     7ea0a000-7ea18000       Deferred        libxext.so.6
ELF     7ea18000-7ea1d000       Deferred        libxxf86vm.so.1
ELF     7ea1d000-7ea35000       Deferred        libice.so.6
ELF     7ea35000-7ea3d000       Deferred        libsm.so.6
ELF     7ea50000-7eadd000       Export          winex11<elf>
  \-PE  7ea60000-7eadd000       \               winex11
ELF     7eb6c000-7eb8c000       Deferred        libexpat.so.1
ELF     7eb8c000-7ebb7000       Deferred        libfontconfig.so.1
ELF     7ebb7000-7ebcc000       Deferred        libz.so.1
ELF     7ebcc000-7ec3c000       Deferred        libfreetype.so.6
ELF     7ec4f000-7ec98000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec98000       \               advapi32
ELF     7ec98000-7ed33000       Export          gdi32<elf>
  \-PE  7ecb0000-7ed33000       \               gdi32
ELF     7ed33000-7ee71000       Export          user32<elf>
  \-PE  7ed50000-7ee71000       \               user32
ELF     7ee71000-7ee86000       Deferred        rundll32<elf>
  \-PE  7ee80000-7ee86000       \               rundll32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d40000-b7d43000       Deferred        libxau.so.6
ELF     b7d43000-b7d4c000       Deferred        libnss_compat.so.2
ELF     b7d4d000-b7d51000       Deferred        libdl.so.2
ELF     b7d51000-b7e9b000       Deferred        libc.so.6
ELF     b7e9c000-b7eb4000       Deferred        libpthread.so.0
ELF     b7ec7000-b7fdb000       Export          libwine.so.1
ELF     b7fdd000-b7ff9000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
wine: wineprefixcreate failed while creating '/home/name/.wine'.
name@name-desktop:~$ wineserver: could not save registry branch to /home/name/.wine-dtETL5/system.reg : No such file or directory
wineserver: could not save registry branch to /home/name/.wine-dtETL5/user.reg : No such file or directory


---

### Post by fragos on 2007-11-04
I installed Wine from the repository and have found no need to configure it.  I used IE4linux to install IE for checking Windows operation of my web sites.  When I execute an EXE file it automatically runs under Wine.  Some work and some don't. The C dive is in the .wine folder and Nautilus can view it.

---

### Post by cegpope on 2007-11-04
I have tried a variety of applications and none of them respond at all, and I am unable to find any sign that wine is operating at all.

I have also discovered that there is no /home/name/.wine folder on my system.

---

### Post by fragos on 2007-11-04
Did you install Wine with Synaptic from the Ubuntu repositories?  Since your bean count is low, you may be new to Linux.  Folders and files with names that start with "." are hidden from view.  To see then in Nautilus do <ctrl>H or in the view menu check "Show hidden files."

---

### Post by cegpope on 2007-11-04
I have been experimenting with Linux on and off for a couple years now, but it was not until about a week ago that I tried Ubuntu. So far, despite this difficulty, and an inability to get the extra buttons working on my Logitec Marble Mouse, my system is working better out of the box than I was ever able to achieve with patches and hacks under Suze of Fedora. Since installing Ubuntu ~5 days ago, I have yet to encounter a need to boot my windows partition, whereas with previous distros I had given up because I was booting back and forth constantly.

In terminal I get "No such file of directory: if I type in "cd /home/name/.wine" and if I am in the file browser it is not present when viewing hidden files.

I have used Synaptic, the Add/Remove Applications utility, and terminal commands in different attempts to install it and none of them are resulting in an installation that functions.

---

### Post by cegpope on 2007-11-07
I never did figure out why wine was not creating it's folders and why it would not function, but I reinstalled Ubuntu from scratch, this time with a 7.10 disc(instead of updating) and not my 7.04 disc and wine works fine.

---

