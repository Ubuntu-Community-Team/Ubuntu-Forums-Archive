---
title: "No Clue where to put this: Installing Visual Basic 6!"
date: 2008-06-17
forum: General Help
---

### Post by Cpuboye11 on 2008-06-17
Hi,

I have no clue where to put this post.. So i put it in general help...

I'm trying to install VB6 (Visual Basic 6)- for windows in Ubuntu. 

I see the cd... And I can open the setup tool- but when i start to press next- it closes.. After trying threw the terminal- 

I get this:

```
kyle@kyle-laptop:~$ cd /media/cdrom0
kyle@kyle-laptop:/media/cdrom0$ dir
ACMBOOT.EXE  IE4CHECK.INI  READMERP.HTM  SAMPLES       VC98
ACMBOOT.LST  INSTALL.HTM   READMESS.HTM  SETUP	       VFP98
AUTORUN.INF  ISHIELD	   READMEVB.HTM  SETUP.EXE     VID98
COMMON	     KEY.DAT	   READMEVC.HTM  SETUP.INI     VS98ECD1.INF
DAOSDK	     MSDESIGN	   READMEVE.HTM  SETUP.TDF     VS98ENT.MIF
DCOM98	     NTSP3	   READMEVF.HTM  SETUPWIZ.INI  VSS
EULA.TXT     OS		   READMEVI.HTM  SHARED
HTMLHELP     READMEDN.HTM  READMEVJ.HTM  SMSINST.EXE
IE4	     READMEDT.HTM  READMEVS.HTM  VB98
kyle@kyle-laptop:/media/cdrom0$ wine setup.exe
kyle@kyle-laptop:/media/cdrom0$ wine: Unhandled page fault on read access to 0x00000000 at address 0x411c09 (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00411c09).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00411c09 ESP:0033b7b0 EBP:00000000 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:7e8c779c EBX:ffffff31 ECX:0033bee4 EDX:00000001
 ESI:00000000 EDI:0000004e
Stack dump:
0x0033b7b0:  0000004e 0033bee4 ffffff31 00411474
0x0033b7c0:  00426498 00010038 00413747 00010038
0x0033b7d0:  0033ce34 0033c6d0 7ed65548 00000001
0x0033b7e0:  0033b810 7ec382db 0000007c 00130420
0x0033b7f0:  0000005c 0033b8dc 00000006 7ec5fcf0
0x0033b800:  7e8ae1cb 7e8c779c 00133760 0013dce0
Backtrace:
=>1 0x00411c09 in vs60wiz (+0x11c09) (0x00000000)
0x00411c09: cmpb	$0x0,0x0(%esi)
Modules:
Module	Address			Debug info	Name (70 modules)
PE	  400000-  48f000	Export          vs60wiz
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e40c000-7e456000	Deferred        riched20<elf>
  \-PE	7e420000-7e456000	\               riched20
ELF	7e456000-7e469000	Deferred        riched32<elf>
  \-PE	7e460000-7e469000	\               riched32
ELF	7e48d000-7e4a0000	Deferred        libresolv.so.2
ELF	7e4ae000-7e4cc000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4cc000	\               iphlpapi
ELF	7e4cc000-7e52d000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e52d000	\               rpcrt4
ELF	7e52d000-7e5d1000	Deferred        ole32<elf>
  \-PE	7e540000-7e5d1000	\               ole32
ELF	7e686000-7e6b9000	Deferred        uxtheme<elf>
  \-PE	7e690000-7e6b9000	\               uxtheme
ELF	7e6b9000-7e6c2000	Deferred        libxcursor.so.1
ELF	7e6c2000-7e6c7000	Deferred        libxfixes.so.3
ELF	7e6c7000-7e6ca000	Deferred        libxcomposite.so.1
ELF	7e6ca000-7e6d0000	Deferred        libxrandr.so.2
ELF	7e6d0000-7e6d8000	Deferred        libxrender.so.1
ELF	7e6d8000-7e6f8000	Deferred        imm32<elf>
  \-PE	7e6e0000-7e6f8000	\               imm32
ELF	7e6f8000-7e6fd000	Deferred        libxdmcp.so.6
ELF	7e6fd000-7e715000	Deferred        libxcb.so.1
ELF	7e715000-7e7fc000	Deferred        libx11.so.6
ELF	7e7fc000-7e80a000	Deferred        libxext.so.6
ELF	7e80a000-7e822000	Deferred        libice.so.6
ELF	7e822000-7e82a000	Deferred        libsm.so.6
ELF	7e838000-7e8cf000	Deferred        winex11<elf>
  \-PE	7e850000-7e8cf000	\               winex11
ELF	7e8f3000-7e914000	Deferred        libexpat.so.1
ELF	7e914000-7e93e000	Deferred        libfontconfig.so.1
ELF	7e93f000-7e944000	Deferred        libxxf86vm.so.1
ELF	7e94c000-7e961000	Deferred        libz.so.1
ELF	7e961000-7e9d1000	Deferred        libfreetype.so.6
ELF	7e9d1000-7e9f2000	Deferred        mpr<elf>
  \-PE	7e9e0000-7e9f2000	\               mpr
ELF	7e9f2000-7ea4b000	Deferred        shlwapi<elf>
  \-PE	7ea00000-7ea4b000	\               shlwapi
ELF	7ea4b000-7eb5e000	Deferred        shell32<elf>
  \-PE	7ea60000-7eb5e000	\               shell32
ELF	7eb5e000-7eb72000	Deferred        lz32<elf>
  \-PE	7eb60000-7eb72000	\               lz32
ELF	7eb72000-7eb8b000	Deferred        version<elf>
  \-PE	7eb80000-7eb8b000	\               version
ELF	7eb8b000-7ebdd000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebdd000	\               advapi32
ELF	7ebdd000-7ec78000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec78000	\               gdi32
ELF	7ec78000-7edbf000	Deferred        user32<elf>
  \-PE	7ec90000-7edbf000	\               user32
ELF	7edbf000-7ee7e000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee7e000	\               comctl32
ELF	7ee7e000-7ee96000	Deferred        libnsl.so.1
ELF	7ee96000-7ee9f000	Deferred        libnss_compat.so.2
ELF	7ee9f000-7eea2000	Deferred        libxinerama.so.1
ELF	7efcd000-7eff2000	Deferred        libm.so.6
ELF	7eff2000-7eff5000	Deferred        libxau.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7cf0000-b7cf2000	Deferred        libxcb-xlib.so.0
ELF	b7cf2000-b7cfc000	Deferred        libnss_nis.so.2
ELF	b7d00000-b7d04000	Deferred        libdl.so.2
ELF	b7d04000-b7e53000	Deferred        libc.so.6
ELF	b7e54000-b7e6c000	Deferred        libpthread.so.0
ELF	b7e7a000-b7fb0000	Deferred        libwine.so.1
ELF	b7fb2000-b7fce000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000018 (D) C:\windows\temp\vs60wiz.exe
	00000019    0 <==
Backtrace:
=>1 0x00411c09 in vs60wiz (+0x11c09) (0x00000000)

kyle@kyle-laptop:/media/cdrom0$ 
```


Any help would be helpful.
Thanks
Kyle

---

### Post by avtolle on 2008-06-17
I don't think you will be successful, as that is a program for Windows. Perhaps I'm not grasping the problem correctly, but unless you are installing it under WINE (if it will work under WINE), it won't install under "Straight Linus". Is there an analogous application for Ubuntu in the repositories?

---

### Post by Cpuboye11 on 2008-06-17
I was talking about or meaning to state that i was attempting to install under Wine. That is why one command states-

wine setup.exe

---

### Post by avtolle on 2008-06-17
Sorry, missed that when I was looking at the output.

---

### Post by Cpuboye11 on 2008-06-17
> **avtolle said:**
> Sorry, missed that when I was looking at the output.

No big deal- lot of code there :-D


I have looked and saw many people stating that VB is to much for Wine to handle. Is this true.. Has any one gotten it to work yet?

---

### Post by avtolle on 2008-06-17
If you've looked and haven't found where anyone has had success, then the odds are great that no one, as of yet, has been able to do it.

---

### Post by igoddard on 2008-06-21
> **Cpuboye11 said:**
> Hi,

I have no clue where to put this post.. So i put it in general help...

I'm trying to install VB6 (Visual Basic 6)- for windows in Ubuntu. 

I see the cd... And I can open the setup tool- but when i start to press next- it closes.. After trying threw the terminal- 

I get this:

```
kyle@kyle-laptop:~$ cd /media/cdrom0
kyle@kyle-laptop:/media/cdrom0$ dir
ACMBOOT.EXE  IE4CHECK.INI  READMERP.HTM  SAMPLES       VC98
ACMBOOT.LST  INSTALL.HTM   READMESS.HTM  SETUP	       VFP98
AUTORUN.INF  ISHIELD	   READMEVB.HTM  SETUP.EXE     VID98
COMMON	     KEY.DAT	   READMEVC.HTM  SETUP.INI     VS98ECD1.INF
DAOSDK	     MSDESIGN	   READMEVE.HTM  SETUP.TDF     VS98ENT.MIF
DCOM98	     NTSP3	   READMEVF.HTM  SETUPWIZ.INI  VSS
EULA.TXT     OS		   READMEVI.HTM  SHARED
HTMLHELP     READMEDN.HTM  READMEVJ.HTM  SMSINST.EXE
IE4	     READMEDT.HTM  READMEVS.HTM  VB98
kyle@kyle-laptop:/media/cdrom0$ wine setup.exe
kyle@kyle-laptop:/media/cdrom0$ wine: Unhandled page fault on read access to 0x00000000 at address 0x411c09 (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00411c09).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00411c09 ESP:0033b7b0 EBP:00000000 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:7e8c779c EBX:ffffff31 ECX:0033bee4 EDX:00000001
 ESI:00000000 EDI:0000004e
Stack dump:
0x0033b7b0:  0000004e 0033bee4 ffffff31 00411474
0x0033b7c0:  00426498 00010038 00413747 00010038
0x0033b7d0:  0033ce34 0033c6d0 7ed65548 00000001
0x0033b7e0:  0033b810 7ec382db 0000007c 00130420
0x0033b7f0:  0000005c 0033b8dc 00000006 7ec5fcf0
0x0033b800:  7e8ae1cb 7e8c779c 00133760 0013dce0
Backtrace:
=>1 0x00411c09 in vs60wiz (+0x11c09) (0x00000000)
0x00411c09: cmpb	$0x0,0x0(%esi)
Modules:
Module	Address			Debug info	Name (70 modules)
PE	  400000-  48f000	Export          vs60wiz
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e40c000-7e456000	Deferred        riched20<elf>
  \-PE	7e420000-7e456000	\               riched20
ELF	7e456000-7e469000	Deferred        riched32<elf>
  \-PE	7e460000-7e469000	\               riched32
ELF	7e48d000-7e4a0000	Deferred        libresolv.so.2
ELF	7e4ae000-7e4cc000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4cc000	\               iphlpapi
ELF	7e4cc000-7e52d000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e52d000	\               rpcrt4
ELF	7e52d000-7e5d1000	Deferred        ole32<elf>
  \-PE	7e540000-7e5d1000	\               ole32
ELF	7e686000-7e6b9000	Deferred        uxtheme<elf>
  \-PE	7e690000-7e6b9000	\               uxtheme
ELF	7e6b9000-7e6c2000	Deferred        libxcursor.so.1
ELF	7e6c2000-7e6c7000	Deferred        libxfixes.so.3
ELF	7e6c7000-7e6ca000	Deferred        libxcomposite.so.1
ELF	7e6ca000-7e6d0000	Deferred        libxrandr.so.2
ELF	7e6d0000-7e6d8000	Deferred        libxrender.so.1
ELF	7e6d8000-7e6f8000	Deferred        imm32<elf>
  \-PE	7e6e0000-7e6f8000	\               imm32
ELF	7e6f8000-7e6fd000	Deferred        libxdmcp.so.6
ELF	7e6fd000-7e715000	Deferred        libxcb.so.1
ELF	7e715000-7e7fc000	Deferred        libx11.so.6
ELF	7e7fc000-7e80a000	Deferred        libxext.so.6
ELF	7e80a000-7e822000	Deferred        libice.so.6
ELF	7e822000-7e82a000	Deferred        libsm.so.6
ELF	7e838000-7e8cf000	Deferred        winex11<elf>
  \-PE	7e850000-7e8cf000	\               winex11
ELF	7e8f3000-7e914000	Deferred        libexpat.so.1
ELF	7e914000-7e93e000	Deferred        libfontconfig.so.1
ELF	7e93f000-7e944000	Deferred        libxxf86vm.so.1
ELF	7e94c000-7e961000	Deferred        libz.so.1
ELF	7e961000-7e9d1000	Deferred        libfreetype.so.6
ELF	7e9d1000-7e9f2000	Deferred        mpr<elf>
  \-PE	7e9e0000-7e9f2000	\               mpr
ELF	7e9f2000-7ea4b000	Deferred        shlwapi<elf>
  \-PE	7ea00000-7ea4b000	\               shlwapi
ELF	7ea4b000-7eb5e000	Deferred        shell32<elf>
  \-PE	7ea60000-7eb5e000	\               shell32
ELF	7eb5e000-7eb72000	Deferred        lz32<elf>
  \-PE	7eb60000-7eb72000	\               lz32
ELF	7eb72000-7eb8b000	Deferred        version<elf>
  \-PE	7eb80000-7eb8b000	\               version
ELF	7eb8b000-7ebdd000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebdd000	\               advapi32
ELF	7ebdd000-7ec78000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec78000	\               gdi32
ELF	7ec78000-7edbf000	Deferred        user32<elf>
  \-PE	7ec90000-7edbf000	\               user32
ELF	7edbf000-7ee7e000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee7e000	\               comctl32
ELF	7ee7e000-7ee96000	Deferred        libnsl.so.1
ELF	7ee96000-7ee9f000	Deferred        libnss_compat.so.2
ELF	7ee9f000-7eea2000	Deferred        libxinerama.so.1
ELF	7efcd000-7eff2000	Deferred        libm.so.6
ELF	7eff2000-7eff5000	Deferred        libxau.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7cf0000-b7cf2000	Deferred        libxcb-xlib.so.0
ELF	b7cf2000-b7cfc000	Deferred        libnss_nis.so.2
ELF	b7d00000-b7d04000	Deferred        libdl.so.2
ELF	b7d04000-b7e53000	Deferred        libc.so.6
ELF	b7e54000-b7e6c000	Deferred        libpthread.so.0
ELF	b7e7a000-b7fb0000	Deferred        libwine.so.1
ELF	b7fb2000-b7fce000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000018 (D) C:\windows\temp\vs60wiz.exe
	00000019    0 <==
Backtrace:
=>1 0x00411c09 in vs60wiz (+0x11c09) (0x00000000)

kyle@kyle-laptop:/media/cdrom0$ 
```


Any help would be helpful.
Thanks
Kyle

This is a Wine bug and I think it may be the same as my bug 11203.  If it is it's the result of a Wine dev assuming that an X server which reports it can only handle 24 bpp (bits per pixel) can actually handle 32 coupled with an app that throws a 32bpp bitmap at it.

Try this:

Follow the instructions on winehq site to install git (if you don't already have it) and download the latest source, build wine and test to check that you still have the bug.  In ~/wine/dlls/winex11.drv edit x11drv_main.c and locate the case 24: statement at line 300.  Add the statement
        return depth;
after this statement and before the case 32; statement (but not in the middle of the comment :) )

Rebuild wine and see if this fixes the problem.  If I'm right it will.  In order to encourage the wine devs to put in a proper fix follow these instructions [http://wiki.winehq.org/MakeTestFailures](http://wiki.winehq.org/MakeTestFailures)
using the uncorrected version and also log a bug with wine.

As a matter of interest, what's your hardware?  Mine's an Advent laptop with Intel graphics H/W.

Ian

---

### Post by myromance123 on 2008-06-21
You could always try alternatives to VB. Here are some I found:

RealBasic at [http://www.realbasic.com](http://www.realbasic.com) (not open source I believe)

HBasic  [http://hbasic.sourceforge.net/](http://hbasic.sourceforge.net/) 

and last but not least(all I know),
Gambas which you'll find in the repositories(supposedly quite good).

Give'em a check if you dont get VB running. It never hurts to try :D

(also heard there is StarBasic for OpenOffice, not sure how that works though)~

---

### Post by igoddard on 2008-06-21
PS to my previous post.

Simply building a new version of wine does not install it as the default version.  It leaves in in ~/wine (where you also run your make commands) and you should run it from there.  First back up your existing .wine directory.  The run

env WINEPREFIX="/home/username/.wine" ./wine whatever.exe

where username is, of course, your username.

If you then want to install your amended version as standard run
sudo make install

Ian

---

### Post by Tux_Johannes on 2008-11-10
Hi, I have a similiar error message Cpuboye11. [click]("http://paste.ubuntuusers.de/392807/")
I'm using Wine 1.1.8 and the bug 11203 seems to be fixed. 

Can anybody help us?

---

### Post by Gary Stout on 2008-12-24
I don't know if you guys ever got this to work, but personally, I have never had good luck with WINE. I have managed to get it to run a few things, but there has always been issues of some sort. 

If you haven't yet tried it, you owe it to yourself to give [www.virtualbox.org](www.virtualbox.org) a try. So far, I haven't found anything yet that it won't run. I have never tried Visual Basic under VB, but I would almost place a bet that it would work. I use another windows based programming language myself and it work flawlessly running under virtual box and Ubuntu. 

I "think" I have VB 6.0......if you want me to install it to test and report back, I will do that so we all know.
Let me know...

Gary

---

### Post by KendzSha on 2009-10-01
i've succesffuly installed VB6 in Ubunto 9.04 using wine. it worked if you use it but there are some glitches and missing components on it in other words you may use it but cant fully develope it specialy when creating simple databse prog... we are still searching and testing until now in tyring to enable its full functions to run in ubunto

---

