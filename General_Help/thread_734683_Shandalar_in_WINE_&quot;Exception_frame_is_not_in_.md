---
title: "Shandalar in WINE: &quot;Exception frame is not in stack limits&quot;"
date: 2008-03-24
forum: General Help
---

### Post by rugglesworth on 2008-03-24
Hello,

I'm trying to run an executable file using Wine.  I'm pretty sure that my Wine is fine, because I run a few other programs through it.  However, when I try to start Shandalar (a computer game), Wine fails.  On the Wine website, there are problems reported regarding gameplay, but I cannot even get that far.  Here is what I put in to the terminal:
```
$ wine '/home/ben/Desktop/shandalar_FILES/Magic/Program/magic.exe'

```
and here is what I get back:
```
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
wine: Unhandled page fault on write access to 0x003d2000 at address 0xab537c (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x003d2000 in 32-bit code (0x00ab537c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00ab537c ESP:00986963 EBP:00ab532c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000900 EBX:00000957 ECX:0000031d EDX:0000031e
 ESI:00a533a2 EDI:003d2000
Stack dump:
0x00986963:  00000900 00000900 00000900 00007100
0x00986973:  00000000 6f6f5400 6e616d20 706f2079
0x00986983:  43206e65 6c617461 3a73676f 78614d20
0x00986993:  0a642520 5c3a4400 6d77654e 63696761
0x009869a3:  756f735c 73656372 64654e5c 64726143
0x009869b3:  7461435c 676f6c61 0000632e 00627200
Backtrace:
=>1 0x00ab537c in drawcardlib (+0x15537c) (0x00ab532c)
  2 0x98655da2 (0x0774903c)
  3 0x00000000 (0x00000000)
0x00ab537c: stosb       %es:(%edi)
Modules:
Module  Address                 Debug info      Name (100 modules)
PE        340000-  357000       Deferred        cdtools
PE        400000-  95b000       Deferred        magic
PE        960000-  ab9000       Export          drawcardlib
PE        ac0000-  be8000       Deferred        cardartlib
PE        bf0000-  df1000       Deferred        deckdll
PE      10000000-10010000       Deferred        manalinkinterface
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cc93000-7cce4000       Deferred        libgcrypt.so.11
ELF     7cce4000-7cce8000       Deferred        libgpg-error.so.0
ELF     7cce8000-7ccf8000       Deferred        libtasn1.so.3
ELF     7ccf8000-7cd00000       Deferred        libkrb5support.so.0
ELF     7cd00000-7cd2e000       Deferred        libcrypt.so.1
ELF     7cd2e000-7cd9e000       Deferred        libgnutls.so.13
ELF     7cd9e000-7cdc3000       Deferred        libk5crypto.so.3
ELF     7cdc3000-7ce4b000       Deferred        libkrb5.so.3
ELF     7ce4b000-7ce74000       Deferred        libgssapi_krb5.so.2
ELF     7ce74000-7cea9000       Deferred        libcups.so.2
ELF     7cecd000-7cee0000       Deferred        libresolv.so.2
ELF     7cee0000-7cee2000       Deferred        libkeyutils.so.1
ELF     7ceeb000-7cf09000       Deferred        iphlpapi<elf>
  \-PE  7cef0000-7cf09000       \               iphlpapi
ELF     7cf09000-7cf62000       Deferred        rpcrt4<elf>
  \-PE  7cf20000-7cf62000       \               rpcrt4
ELF     7cf62000-7d003000       Deferred        ole32<elf>
  \-PE  7cf70000-7d003000       \               ole32
ELF     7d08d000-7d0a2000       Deferred        midimap<elf>
  \-PE  7d090000-7d0a2000       \               midimap
ELF     7d0a2000-7d0c9000       Deferred        msacm32<elf>
  \-PE  7d0b0000-7d0c9000       \               msacm32
ELF     7d0c9000-7d0e1000       Deferred        msacm32<elf>
  \-PE  7d0d0000-7d0e1000       \               msacm32
ELF     7d0e1000-7d1a7000       Deferred        libasound.so.2
ELF     7d1a7000-7d1dd000       Deferred        winealsa<elf>
  \-PE  7d1b0000-7d1dd000       \               winealsa
ELF     7d1dd000-7d20f000       Deferred        uxtheme<elf>
  \-PE  7d1e0000-7d20f000       \               uxtheme
ELF     7d20f000-7d218000       Deferred        libxcursor.so.1
ELF     7d218000-7d235000       Deferred        imm32<elf>
  \-PE  7d220000-7d235000       \               imm32
ELF     7d235000-7d23d000       Deferred        libxrender.so.1
ELF     7e248000-7e491000       Deferred        i915_dri.so
ELF     7e491000-7e49b000       Deferred        libdrm.so.2
ELF     7e49b000-7e4a0000       Deferred        libxfixes.so.3
ELF     7e4a0000-7e4a3000       Deferred        libxdamage.so.1
ELF     7e4a3000-7e504000       Deferred        libgl.so.1
ELF     7e504000-7e509000       Deferred        libxdmcp.so.6
ELF     7e509000-7e50c000       Deferred        libxau.so.6
ELF     7e50c000-7e5fd000       Deferred        libx11.so.6
ELF     7e5fd000-7e60b000       Deferred        libxext.so.6
ELF     7e60b000-7e610000       Deferred        libxxf86vm.so.1
ELF     7e610000-7e628000       Deferred        libice.so.6
ELF     7e628000-7e630000       Deferred        libsm.so.6
ELF     7e630000-7e633000       Deferred        libcom_err.so.2
ELF     7e635000-7e63b000       Deferred        libxrandr.so.2
ELF     7e63b000-7e6c6000       Deferred        winex11<elf>
  \-PE  7e650000-7e6c6000       \               winex11
ELF     7e74c000-7e76c000       Deferred        libexpat.so.1
ELF     7e76c000-7e797000       Deferred        libfontconfig.so.1
ELF     7e797000-7e7ac000       Deferred        libz.so.1
ELF     7e7ac000-7e81c000       Deferred        libfreetype.so.6
ELF     7e827000-7e88f000       Deferred        msvcrt<elf>
  \-PE  7e840000-7e88f000       \               msvcrt
ELF     7e88f000-7e8a3000       Deferred        lz32<elf>
  \-PE  7e8a0000-7e8a3000       \               lz32
ELF     7e8a3000-7e8bd000       Deferred        version<elf>
  \-PE  7e8b0000-7e8bd000       \               version
ELF     7e8bd000-7e8f2000       Deferred        winspool<elf>
  \-PE  7e8d0000-7e8f2000       \               winspool
ELF     7e8f2000-7e94b000       Deferred        shlwapi<elf>
  \-PE  7e900000-7e94b000       \               shlwapi
ELF     7e94b000-7ea4e000       Deferred        shell32<elf>
  \-PE  7e960000-7ea4e000       \               shell32
ELF     7ea4e000-7eaef000       Deferred        comdlg32<elf>
  \-PE  7ea60000-7eaef000       \               comdlg32
ELF     7eaef000-7eb16000       Deferred        msvfw32<elf>
  \-PE  7eb00000-7eb16000       \               msvfw32
ELF     7eb16000-7eba4000       Deferred        winmm<elf>
  \-PE  7eb20000-7eba4000       \               winmm
ELF     7eba4000-7ebed000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebed000       \               advapi32
ELF     7ebed000-7ec88000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec88000       \               gdi32
ELF     7ec88000-7edc6000       Deferred        user32<elf>
  \-PE  7eca0000-7edc6000       \               user32
ELF     7edc6000-7ee84000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee84000       \               comctl32
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efb8000       Deferred        libnss_nis.so.2
ELF     7efb8000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cd6000-b7cda000       Deferred        libdl.so.2
ELF     b7cda000-b7e24000       Deferred        libc.so.6
ELF     b7e25000-b7e3d000       Deferred        libpthread.so.0
ELF     b7e48000-b7f5c000       Deferred        libwine.so.1
ELF     b7f5e000-b7f7a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\ben\Desktop\shandalar_FILES\Magic\Program\magic.exe
        00000009    0 <==
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```
Any help is appreciated.

Ben

---

### Post by perillux on 2008-07-21
I am also trying to play this game.

I get this error when I try to run the game:
> err:module:attach_process_dlls "CardArtLib.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MTG\\Magic\\Magic.exe" failed, status 39635a

Did the installer work for you?  Because it didn't for me, I had to download the game.  Also, if your not using "Manalink" you should get it.  It's the newest version of the game.  Might fix a few of your errors.

---

