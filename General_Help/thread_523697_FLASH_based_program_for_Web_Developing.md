---
title: "FLASH based program for Web Developing"
date: 2007-08-12
forum: General Help
---

### Post by Gales on 2007-08-12
Hello

I'm currently involved in a project relating in creating a Website using Linux Ubuntu. I want to create a user interface for the site, preferably using a Flash-based program. I've gone through most of the forum and can't find any suitable software.

Can anyone tell me the best Flash-based porgram that works best with Ubuntu for web developing?

Thanks in advance!

---

### Post by kellemes on 2007-08-12
There is F4L (FlashForLinux) but is simply sucks.

Adobe Flash is king in this area.
If you're serious about Flash-development, boot Windows and buy Adobe Flash and preferably Dreamweaver.

---

### Post by Gales on 2007-08-12
That's the problem. We cannot use Windows. We are trying to develop a system completely independent of Windows. By using Linux Ubuntu we are trying to show that Linux can preform as good as Windows can.

---

### Post by kellemes on 2007-08-12
> **Gales said:**
> That's the problem. We cannot use Windows. We are trying to develop a system completely independent of Windows. By using Linux Ubuntu we are trying to show that Linux can preform as good as Windows can.

Well, I do think GNU/Linux can perform as good as Windows, but this does not mean it can do everything Windows does I'm  afraid (and vice versa).
Flashdevelopment is one of many areas where GNU/Linux has little to nothing to offer.
If it's about showing-of GNU/Linux as a development platform for great looking websites you could focus on DHTML/AJAX as an alternative.
If it's about creating animations/movies on GNU/Linux there are a couple of tools available but not many, and certainly not as many as for Windows, and the quality is less also..

But it could be I'm wrong and there indeed are great Flasheditors, don't think so though..

---

### Post by yorik on 2007-08-12
I've also looked for some way to do flash under Linux but i haven't found anything good so far.
But i was very flash-dependant, now all this made me rediscover the value and power of finely-designed html...
I've heard adobe flash works pretty well under wine, though.

---

### Post by Gales on 2007-08-12
Really? Adobe works under Wine? How to install that?

I've tried to install Adobe Flash with wine, but no success. It cannot run in my Linux Ubuntu

---

### Post by kellemes on 2007-08-12
[http://appdb.winehq.org/appview.php?iAppId=23]("http://appdb.winehq.org/appview.php?iAppId=23")

It depends on the version if you have a chance of getting it to work.

---

### Post by venoom27 on 2007-08-15
I know this is probable not the place for it but I posted this on the Wine Flash 8 support site and no one respond to it. But every time I run Flash 8 I get the splash screen and when it is building workspaces it crashes and gives the code below. I have tried and tried and cannot get it to work can anyone help me? Thanks



$ wine '/home/john/.wine/drive_c/Program Files/Macromedia/Flash 8/Flash.exe'
err:shell:SHGetFileInfoW pidl is null!
fixme:wintab32:WTInfoW (0, 0, (nil)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:imm:ImmSetCandidateWindow (0x192b78, 0x33be00): stub
fixme:imm:ImmReleaseContext (0x100ce, 0x192b78): stub
fixme:imm:ImmReleaseContext (0x100ce, 0x192b78): stub
wine: Unhandled page fault on read access to 0x000007e0 at address 0x7e0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000007e0 in 32-bit code (0x000007e0).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:000007e0 ESP:0033e99c EBP:00000000 EFLAGS:00210212( - 00 - RIA1)
EAX:0000010a EBX:000003ef ECX:00000014 EDX:00000014
ESI:00001f24 EDI:01430478
Stack dump:
0x0033e99c: 0000001f 00001f24 0033eb0c 0033ea94
0x0033e9ac: 00000014 04e338c8 00cb24a3 00001f08
0x0033e9bc: 000003ef 00000000 05416b00 05416b00
0x0033e9cc: 0033eb0c 01b57b9f 00ccb2a3 01880000
0x0033e9dc: 00000000 00000001 0440eb64 00000000
0x0033e9ec: 00000000 01016b08 00001f14 00000000
Backtrace:
=>1 0x000007e0 (0x00000000)
0x000007e0: addb %al,0x0(%eax)
Modules:
Module Address Debug info Name (120 modules)
PE 350000- 358000 Deferred emlaunch
PE 3f0000- 3f7000 Deferred flfile
PE 400000- 154d000 Deferred flash
PE 1990000- 1d52000 Deferred flashresources
PE 1d60000- 1e63000 Deferred mfc71
PE 4c80000- 4d82000 Deferred mfc71u
PE 10000000-1022f000 Deferred flash_8_video_extension
PE 12000000-121ae000 Deferred xerces-c_2_6
PE 13000000-13191000 Deferred mmxptresources
PE 30000000-30256000 Deferred authplay
ELF 7b800000-7b929000 Deferred kernel32
\-PE 7b820000-7b929000 \ kernel32
ELF 7bc00000-7bc97000 Deferred ntdll
\-PE 7bc10000-7bc97000 \ ntdll
ELF 7bf00000-7bf03000 Deferred
PE 7c340000-7c396000 Deferred msvcr71
ELF 7c3da000-7c3f9000 Deferred wintab32
\-PE 7c3e0000-7c3f9000 \ wintab32
ELF 7c54e000-7c56e000 Deferred mlang
\-PE 7c560000-7c56e000 \ mlang
ELF 7c56e000-7c5c1000 Deferred crypt32
\-PE 7c580000-7c5c1000 \ crypt32
ELF 7c5c1000-7c5db000 Deferred wsock32
\-PE 7c5d0000-7c5db000 \ wsock32
ELF 7c5db000-7c5f0000 Deferred midimap
\-PE 7c5e0000-7c5f0000 \ midimap
ELF 7c5f0000-7c608000 Deferred msacm32
\-PE 7c600000-7c608000 \ msacm32
ELF 7c608000-7c644000 Deferred wineoss
\-PE 7c610000-7c644000 \ wineoss
ELF 7c644000-7c695000 Deferred libgcrypt.so.11
ELF 7c695000-7c6aa000 Deferred libtasn1.so.3
ELF 7c6aa000-7c6d8000 Deferred libcrypt.so.1
ELF 7c6eb000-7c75b000 Deferred libgnutls.so.13
ELF 7cc61000-7cc65000 Deferred libgpg-error.so.0
ELF 7cc65000-7cc96000 Deferred libcups.so.2
ELF 7cd65000-7cd97000 Deferred uxtheme
\-PE 7cd70000-7cd97000 \ uxtheme
ELF 7cd99000-7cd9e000 Deferred libxfixes.so.3
ELF 7cd9e000-7cda7000 Deferred libxcursor.so.1
ELF 7cda7000-7cdad000 Deferred libxrandr.so.2
ELF 7cdad000-7cdb5000 Deferred libxrender.so.1
ELF 7ddb5000-7e00b000 Deferred i915_dri.so
ELF 7e00b000-7e014000 Deferred libdrm.so.2
ELF 7e014000-7e074000 Deferred libgl.so.1
ELF 7e074000-7e079000 Deferred libxdmcp.so.6
ELF 7e079000-7e07c000 Deferred libxau.so.6
ELF 7e07c000-7e16d000 Deferred libx11.so.6
ELF 7e16d000-7e185000 Deferred libice.so.6
ELF 7e185000-7e20e000 Deferred winex11
\-PE 7e190000-7e20e000 \ winex11
ELF 7e38b000-7e3ab000 Deferred libexpat.so.1
ELF 7e3ab000-7e3d6000 Deferred libfontconfig.so.1
ELF 7e3d6000-7e3ea000 Deferred libz.so.1
ELF 7e3ea000-7e455000 Deferred libfreetype.so.6
ELF 7e455000-7e477000 Deferred oledlg
\-PE 7e460000-7e477000 \ oledlg
ELF 7e477000-7e497000 Deferred mpr
\-PE 7e480000-7e497000 \ mpr
ELF 7e497000-7e4e0000 Deferred wininet
\-PE 7e4a0000-7e4e0000 \ wininet
ELF 7e4e0000-7e50d000 Deferred ws2_32
\-PE 7e4f0000-7e50d000 \ ws2_32
ELF 7e50d000-7e5aa000 Deferred oleaut32
\-PE 7e520000-7e5aa000 \ oleaut32
ELF 7e5aa000-7e5be000 Deferred msimg32
\-PE 7e5b0000-7e5be000 \ msimg32
ELF 7e5be000-7e5db000 Deferred imm32
\-PE 7e5d0000-7e5db000 \ imm32
ELF 7e5db000-7e5f0000 Deferred psapi
\-PE 7e5e0000-7e5f0000 \ psapi
ELF 7e5f0000-7e603000 Deferred libresolv.so.2
ELF 7e603000-7e621000 Deferred iphlpapi
\-PE 7e610000-7e621000 \ iphlpapi
ELF 7e621000-7e67a000 Deferred rpcrt4
\-PE 7e630000-7e67a000 \ rpcrt4
ELF 7e67a000-7e719000 Deferred ole32
\-PE 7e690000-7e719000 \ ole32
ELF 7e719000-7e740000 Deferred msvfw32
\-PE 7e720000-7e740000 \ msvfw32
ELF 7e740000-7e766000 Deferred msacm32
\-PE 7e750000-7e766000 \ msacm32
ELF 7e766000-7e7a0000 Deferred avifil32
\-PE 7e770000-7e7a0000 \ avifil32
ELF 7e7a0000-7e82e000 Deferred winmm
\-PE 7e7b0000-7e82e000 \ winmm
ELF 7e82e000-7e842000 Deferred lz32
\-PE 7e830000-7e842000 \ lz32
ELF 7e842000-7e85c000 Deferred version
\-PE 7e850000-7e85c000 \ version
ELF 7e85c000-7e88f000 Deferred winspool
\-PE 7e860000-7e88f000 \ winspool
ELF 7e88f000-7e930000 Deferred comdlg32
\-PE 7e8a0000-7e930000 \ comdlg32
ELF 7e930000-7e9ed000 Deferred comctl32
\-PE 7e940000-7e9ed000 \ comctl32
ELF 7e9ed000-7eb2a000 Deferred user32
\-PE 7ea10000-7eb2a000 \ user32
ELF 7eb2a000-7eb83000 Deferred shlwapi
\-PE 7eb40000-7eb83000 \ shlwapi
ELF 7eb83000-7ec81000 Deferred shell32
\-PE 7eb90000-7ec81000 \ shell32
ELF 7ec81000-7ec8d000 Deferred libgcc_s.so.1
ELF 7ec8d000-7ec9b000 Deferred libxext.so.6
ELF 7ec9b000-7eca0000 Deferred libxxf86vm.so.1
ELF 7ed8a000-7ee4a000 Deferred gdi32
\-PE 7eda0000-7ee4a000 \ gdi32
ELF 7ee4a000-7ee92000 Deferred advapi32
\-PE 7ee60000-7ee92000 \ advapi32
ELF 7efa4000-7efaf000 Deferred libnss_files.so.2
ELF 7efaf000-7efc6000 Deferred libnsl.so.1
ELF 7efc6000-7efed000 Deferred libm.so.6
ELF 7efed000-7eff6000 Deferred libsm.so.6
ELF 7eff6000-7f000000 Deferred libnss_nis.so.2
ELF b7d25000-b7d2e000 Deferred libnss_compat.so.2
ELF b7d2f000-b7d33000 Deferred libdl.so.2
ELF b7d33000-b7e74000 Deferred libc.so.6
ELF b7e75000-b7e8c000 Deferred libpthread.so.0
ELF b7e9f000-b7fb3000 Deferred libwine.so.1
ELF b7fb5000-b7fd0000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000a
0000000c 0
0000000b 0
00000008 (D) C:\Program Files\Macromedia\Flash 8\Flash.exe
0000000f 0
0000000e 0
0000000d 15
00000009 0

---

