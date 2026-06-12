---
title: "How Do I install internet explorer through wine?"
date: 2005-10-28
forum: General Help
---

### Post by eyebrowman92 on 2005-10-28
ive tries installing internet explorer through wine but it doesnt seem to work. instead a dialog boxs pops up saying, "setup was unable to download the requiered components.  make sure you are connected to the internet, or try setup again later."  i know im connected to the internet, and ive tried setup a million times. if someone could help me out on this id appreciate it. thanks.

P.S.-i want to install ie for shockwave purposes.

---

### Post by mhancoc7 on 2005-10-28
Have you tryed the sidenet wine setup. Check it out here:
[http://www.frankscorner.org/index.php?p=sidenet]("http://www.frankscorner.org/index.php?p=sidenet")

It work very easily for me. I hope that helps.

God Bless, Jereme

---

### Post by eyebrowman92 on 2005-10-28
would there be a way to install it through a terminal? i dont know how to use synaptic or anything else very well.

---

### Post by aysiu on 2005-10-28
I found this the easiest way to install IE through Wine:

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

---

### Post by eyebrowman92 on 2005-10-28
thanks but i cant figure out excactly how to download. could you help me?

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]thanks but i cant figure out excactly how to download. could you help me?[/QUOTE] One of the first things on the page is > The newest IEs4Linux version is 1.0 (download now). Click on the part that says "download now." Extract the .tar.gz. Then, double-click on the file called *ies4linux* and choose to run it in terminal. You have to have Wine installed first, though. Do you have Wine?

---

### Post by eyebrowman92 on 2005-10-28
yes i have wine. at least i think. i did type in a terminal sudo apt-get install wine and it worked. so yes.

---

### Post by eyebrowman92 on 2005-10-28
im sorry im putting you through all this trouble but i just started using linux about 2 weeks ago and im not sure how to do any of this stuff.  from firefox i open it in the archive manager right?

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]im sorry im putting you through all this trouble but i just started using linux about 2 weeks ago and im not sure how to do any of this stuff.  from firefox i open it in the archive manager right?[/QUOTE] Download it to your desktop. Then double-click it. Click **Extract**. A new (regular-looking) folder should appear. Within that folder is a file called *ies4linux.sh*. Double-click it. A dialogue with these options will pop up:

Run
Run in terminal
Display
Cancel

Not necessarily in that order, though. Select *Run in terminal*. Watch the sparks fly. To run it, press alt-F2 and type the command *ie6*.

---

### Post by eyebrowman92 on 2005-10-28
lmao ive done all youre telling me and its not working. when i press alt-f2 then ie6 it says "Cannot display location 'file://ie6'

Details: There is no default action associated with this location."

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]lmao ive done all youre telling me and its not working. when i press alt-f2 then ie6 it says "Cannot display location 'file://ie6'

Details: There is no default action associated with this location."[/QUOTE] Hm. Well, did the first part work--running the ies4linux script in terminal? It may not have installed to /usr/bin. I'm trying to remember whether I had to copy it there or it just installed there. Can you type this command in the terminal? ```
locate ie6
```

---

### Post by eyebrowman92 on 2005-10-28
yeah i did and nothing happened. ```
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$


```  


and when i ran it ies4linux in a terminal, the terminal popped up for less than a scond and dissappeared.

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]yeah i did and nothing happened. ```
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$ locate ie6
justin@ubuntu:~$


```[/QUOTE] Something's wrong, then. This is what mine turned up ```
locate ie6
/usr/share/services/useragentstrings/ie60oncurrent.desktop
/usr/share/services/useragentstrings/ie60onwinnt51.desktop
/usr/bin/ie6
/root/.ies4linux/downloads/ie60.exe
/root/.ies4linux/ie6
/root/.ies4linux/ie6/dosdevices
/root/.ies4linux/ie6/dosdevices/c:
/root/.ies4linux/ie6/dosdevices/z:
/root/.ies4linux/ie6/drive_c
/root/.ies4linux/ie6/drive_c/My Documents
/root/.ies4linux/ie6/drive_c/My Documents/My Music
/root/.ies4linux/ie6/drive_c/My Documents/My Pictures
/root/.ies4linux/ie6/drive_c/My Documents/My Video
/root/.ies4linux/ie6/drive_c/Program Files
/root/.ies4linux/ie6/drive_c/Program Files/Common Files
/root/.ies4linux/ie6/drive_c/Program Files/Internet Explorer
/root/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE
/root/.ies4linux/ie6/drive_c/windows
/root/.ies4linux/ie6/drive_c/windows/command
/root/.ies4linux/ie6/drive_c/windows/command/start.exe
/root/.ies4linux/ie6/drive_c/windows/fonts
/root/.ies4linux/ie6/drive_c/windows/fonts/AndaleMo.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/AriBlk.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Comicbd.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Comic.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Georgiab.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Georgiai.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Georgia.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Georgiaz.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Impact.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Trebucbd.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Trebucbi.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Trebucit.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Trebuc.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Verdanab.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Verdanai.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Verdana.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Verdanaz.TTF
/root/.ies4linux/ie6/drive_c/windows/fonts/Webdings.TTF
/root/.ies4linux/ie6/drive_c/windows/inf
/root/.ies4linux/ie6/drive_c/windows/inf/wine.inf
/root/.ies4linux/ie6/drive_c/windows/inf/dcom98.inf
/root/.ies4linux/ie6/drive_c/windows/profiles
/root/.ies4linux/ie6/drive_c/windows/profiles/Administrator
/root/.ies4linux/ie6/drive_c/windows/profiles/root
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Temporary Internet Files
/root/.ies4linux/ie6/drive_c/windows/profiles/root/History
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Cookies
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Start Menu
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Start Menu/Programs
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Start Menu/Programs/StartUp
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Favorites
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Recent
/root/.ies4linux/ie6/drive_c/windows/profiles/root/SendTo
/root/.ies4linux/ie6/drive_c/windows/profiles/root/NetHood
/root/.ies4linux/ie6/drive_c/windows/profiles/root/Templates
/root/.ies4linux/ie6/drive_c/windows/profiles/root/PrintHood
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu/Programs
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Desktop
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Favorites
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Application Data
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Templates
/root/.ies4linux/ie6/drive_c/windows/profiles/All Users/Documents
/root/.ies4linux/ie6/drive_c/windows/Start Menu
/root/.ies4linux/ie6/drive_c/windows/Start Menu/Programs
/root/.ies4linux/ie6/drive_c/windows/Start Menu/Programs/Startup
/root/.ies4linux/ie6/drive_c/windows/Application Data
/root/.ies4linux/ie6/drive_c/windows/system
/root/.ies4linux/ie6/drive_c/windows/system/wcmd.exe
/root/.ies4linux/ie6/drive_c/windows/system/control.exe
/root/.ies4linux/ie6/drive_c/windows/system/help.exe
/root/.ies4linux/ie6/drive_c/windows/system/msiexec.exe
/root/.ies4linux/ie6/drive_c/windows/system/notepad.exe
/root/.ies4linux/ie6/drive_c/windows/system/progman.exe
/root/.ies4linux/ie6/drive_c/windows/system/regsvr32.exe
/root/.ies4linux/ie6/drive_c/windows/system/winmine.exe
/root/.ies4linux/ie6/drive_c/windows/system/winver.exe
/root/.ies4linux/ie6/drive_c/windows/system/asycfilt.dll
/root/.ies4linux/ie6/drive_c/windows/system/comcat.dll
/root/.ies4linux/ie6/drive_c/windows/system/compobj.dll
/root/.ies4linux/ie6/drive_c/windows/system/imagehlp.dll
/root/.ies4linux/ie6/drive_c/windows/system/iprop.dll
/root/.ies4linux/ie6/drive_c/windows/system/ole2.dll
/root/.ies4linux/ie6/drive_c/windows/system/ole32.dll
/root/.ies4linux/ie6/drive_c/windows/system/oleaut32.dll
/root/.ies4linux/ie6/drive_c/windows/system/olecnv32.dll
/root/.ies4linux/ie6/drive_c/windows/system/olepro32.dll
/root/.ies4linux/ie6/drive_c/windows/system/olethk32.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcltc1.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcltc5.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcltccm.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpclts5.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcltscm.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcmqcl.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcmqsvr.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcns4.dll
/root/.ies4linux/ie6/drive_c/windows/system/rpcrt4.dll
/root/.ies4linux/ie6/drive_c/windows/system/secur32.dll
/root/.ies4linux/ie6/drive_c/windows/system/storage.dll
/root/.ies4linux/ie6/drive_c/windows/system/stdole2.tlb
/root/.ies4linux/ie6/drive_c/windows/system/stdole32.tlb
/root/.ies4linux/ie6/drive_c/windows/system/dllhost.exe
/root/.ies4linux/ie6/drive_c/windows/system/install.exe
/root/.ies4linux/ie6/drive_c/windows/system/rpcss.exe
/root/.ies4linux/ie6/drive_c/windows/system/riched20.dll
/root/.ies4linux/ie6/drive_c/windows/system/ACTXPRXY.DLL
/root/.ies4linux/ie6/drive_c/windows/system/APPS.HLP
/root/.ies4linux/ie6/drive_c/windows/system/ATL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/BINDFILE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/BROWSELC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/BROWSEUI.DLL
/root/.ies4linux/ie6/drive_c/windows/system/BROWSEWM.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CERTMGR.MSC
/root/.ies4linux/ie6/drive_c/windows/system/CKCNV.EXE
/root/.ies4linux/ie6/drive_c/windows/system/CORPOL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CRYPT32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CRYPTDLG.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CRYPTEXT.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CRYPTNET.DLL
/root/.ies4linux/ie6/drive_c/windows/system/CRYPTUI.DLL
/root/.ies4linux/ie6/drive_c/windows/system/csseqchk.dll
/root/.ies4linux/ie6/drive_c/windows/system/DHTMLED.OCX
/root/.ies4linux/ie6/drive_c/windows/system/DIGEST.DLL
/root/.ies4linux/ie6/drive_c/windows/system/DISPEX.DLL
/root/.ies4linux/ie6/drive_c/windows/system/DSSBASE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/DSSSIG.EXE
/root/.ies4linux/ie6/drive_c/windows/system/DW15.EXE
/root/.ies4linux/ie6/drive_c/windows/system/DWINTL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/DXTMSFT.DLL
/root/.ies4linux/ie6/drive_c/windows/system/DXTRANS.DLL
/root/.ies4linux/ie6/drive_c/windows/system/enhsig.dll
/root/.ies4linux/ie6/drive_c/windows/system/EXTRAC32.EXE
/root/.ies4linux/ie6/drive_c/windows/system/FIXIE.INF
/root/.ies4linux/ie6/drive_c/windows/system/HLINK.DLL
/root/.ies4linux/ie6/drive_c/windows/system/HMMAPI.DLL
/root/.ies4linux/ie6/drive_c/windows/system/HTML32.CNV
/root/.ies4linux/ie6/drive_c/windows/system/IE_1.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IE_2.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IE_3.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IE_4.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IE4UINIT.EXE
/root/.ies4linux/ie6/drive_c/windows/system/IE_5.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IE_6.CAB
/root/.ies4linux/ie6/drive_c/windows/system/IEDKCS32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/iedom.inf
/root/.ies4linux/ie6/drive_c/windows/system/IEFILES5.INF
/root/.ies4linux/ie6/drive_c/windows/system/IEINFO5.MOF
/root/.ies4linux/ie6/drive_c/windows/system/IEINFO5.OCX
/root/.ies4linux/ie6/drive_c/windows/system/IEJIT.HTM
/root/.ies4linux/ie6/drive_c/windows/system/IEPEERS.DLL
/root/.ies4linux/ie6/drive_c/windows/system/IERNONCE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/iesetup.dll
/root/.ies4linux/ie6/drive_c/windows/system/IEUINIT.INF
/root/.ies4linux/ie6/drive_c/windows/system/IMGUTIL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/INETCPLC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/INETCPL.CPL
/root/.ies4linux/ie6/drive_c/windows/system/INITPKI.DLL
/root/.ies4linux/ie6/drive_c/windows/system/inseng.dll
/root/.ies4linux/ie6/drive_c/windows/system/INSTRSA.DLL
/root/.ies4linux/ie6/drive_c/windows/system/INSTSCH.DLL
/root/.ies4linux/ie6/drive_c/windows/system/JITALERT.GIF
/root/.ies4linux/ie6/drive_c/windows/system/JOBEXEC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/JSCRIPT.DLL
/root/.ies4linux/ie6/drive_c/windows/system/license.txt
/root/.ies4linux/ie6/drive_c/windows/system/LOADWC.EXE
/root/.ies4linux/ie6/drive_c/windows/system/MLANG.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MMUTILSE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSCAT32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSCONV97.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSDATSRC.TLB
/root/.ies4linux/ie6/drive_c/windows/system/MSENCODE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSHTA.EXE
/root/.ies4linux/ie6/drive_c/windows/system/MSHTML.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSHTMLED.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSHTMLER.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSHTML.TLB
/root/.ies4linux/ie6/drive_c/windows/system/MSLS31.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSOSS.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSRATELC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSRATING.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSSIGN32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSSIP32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSTIME.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXML3A.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXML3.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXML3R.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXMLA.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXML.DLL
/root/.ies4linux/ie6/drive_c/windows/system/MSXMLR.DLL
/root/.ies4linux/ie6/drive_c/windows/system/OCCACHE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/PLUGIN.OCX
/root/.ies4linux/ie6/drive_c/windows/system/PSBASE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/PSTOREC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/PSTORERC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/PSTORES.EXE
/root/.ies4linux/ie6/drive_c/windows/system/RELATED.HTM
/root/.ies4linux/ie6/drive_c/windows/system/removbak.inf
/root/.ies4linux/ie6/drive_c/windows/system/RSABASE.DLL
/root/.ies4linux/ie6/drive_c/windows/system/RSACI.RAT
/root/.ies4linux/ie6/drive_c/windows/system/rsaenh.dll
/root/.ies4linux/ie6/drive_c/windows/system/RSASIG.DLL
/root/.ies4linux/ie6/drive_c/windows/system/sch128c.dll
/root/.ies4linux/ie6/drive_c/windows/system/SCROBJ.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SECAUTH.HLP
/root/.ies4linux/ie6/drive_c/windows/system/SENDMAIL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHD401LC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHDOC401.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHDOCLC.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHDOCVW.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHFOLDER.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SHLWAPI.DLL
/root/.ies4linux/ie6/drive_c/windows/system/SIMPDATA.TLB
/root/.ies4linux/ie6/drive_c/windows/system/SOFTPUB.DLL
/root/.ies4linux/ie6/drive_c/windows/system/START.WAV
/root/.ies4linux/ie6/drive_c/windows/system/support.txt
/root/.ies4linux/ie6/drive_c/windows/system/THUMBVW.DLL
/root/.ies4linux/ie6/drive_c/windows/system/TIP.HTM
/root/.ies4linux/ie6/drive_c/windows/system/TIPS.GIF
/root/.ies4linux/ie6/drive_c/windows/system/TRIEDIT.DLL
/root/.ies4linux/ie6/drive_c/windows/system/URLMON.DLL
/root/.ies4linux/ie6/drive_c/windows/system/USERSTUB.EXE
/root/.ies4linux/ie6/drive_c/windows/system/WALLPAPR.HTM
/root/.ies4linux/ie6/drive_c/windows/system/WININET.DLL
/root/.ies4linux/ie6/drive_c/windows/system/WINTRUST.DLL
/root/.ies4linux/ie6/drive_c/windows/system/WLDAP32.DLL
/root/.ies4linux/ie6/drive_c/windows/system/XENROLL.DLL
/root/.ies4linux/ie6/drive_c/windows/system/cscript.exe
/root/.ies4linux/ie6/drive_c/windows/system/dispex.dll
/root/.ies4linux/ie6/drive_c/windows/system/jscript.dll
/root/.ies4linux/ie6/drive_c/windows/system/scr56en.cat
/root/.ies4linux/ie6/drive_c/windows/system/scr56en.inf
/root/.ies4linux/ie6/drive_c/windows/system/scrobj.dll
/root/.ies4linux/ie6/drive_c/windows/system/scrrun.dll
/root/.ies4linux/ie6/drive_c/windows/system/vbscript.dll
/root/.ies4linux/ie6/drive_c/windows/system/wscript.exe
/root/.ies4linux/ie6/drive_c/windows/system/wscript.hlp
/root/.ies4linux/ie6/drive_c/windows/system/wshcon.dll
/root/.ies4linux/ie6/drive_c/windows/system/wshext.dll
/root/.ies4linux/ie6/drive_c/windows/system/wshom.ocx
/root/.ies4linux/ie6/drive_c/windows/system/pngfilt.dll
/root/.ies4linux/ie6/drive_c/windows/temp
/root/.ies4linux/ie6/drive_c/windows/notepad.exe
/root/.ies4linux/ie6/drive_c/windows/regedit.exe
/root/.ies4linux/ie6/drive_c/windows/rundll32.exe
/root/.ies4linux/ie6/drive_c/windows/uninstall.exe
/root/.ies4linux/ie6/drive_c/windows/winhelp.exe
/root/.ies4linux/ie6/drive_c/windows/winhlp32.exe
/root/.ies4linux/ie6/drive_c/windows/winebrowser.exe
/root/.ies4linux/ie6/drive_c/windows/win.ini
/root/.ies4linux/ie6/drive_c/windows/system.ini
/root/.ies4linux/ie6/config
/root/.ies4linux/ie6/system.reg
/root/.ies4linux/ie6/userdef.reg
/root/.ies4linux/ie6/user.reg
/root/.ies4linux/ie6/ies4linux.log
/root/bin/ie6
``` > and when i ran it ies4linux in a terminal, the terminal popped up for less than a scond and dissappeared. Something's wrong, then. It should display a script being executed. You're sure you have Wine installed? What happens when you type this in a terminal? ```
man wine
```

---

### Post by eyebrowman92 on 2005-10-28
..ok so what should i do.  lol i dont know if this means anything but the ies4linux.sh file said i was a text file. idk

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]..ok so what should i do.  lol i dont know if this means anything but the ies4linux.sh file said i was a text file. idk[/QUOTE] Let's make sure you have Wine installed. What happens when you type in ```
man wine
```?

---

### Post by eyebrowman92 on 2005-10-28
```
WINE(1)                         Windows On Unix                        WINE(1)

NAME
       wine - run Windows programs on Unix

SYNOPSIS
       wine program [arguments ... ]
       wine --help
       wine --version

       For  instructions  on passing arguments to Windows programs, please see
       the PROGRAM/ARGUMENTS section of the man page.

DESCRIPTION
       wine loads and runs the given program, where the program is a DOS, Win&#8208;
       dows 3.x, or Win32 executable (x86 binaries only).

       For debugging wine, use winedbg instead.

       For running CUI executables (Windows console programs), use wineconsole
       instead of wine.  This will display all the output in a  separate  win&#8208;
       dows (this requires X11 to run). Not using wineconsole for CUI programs
       will only provide very limited console support, and your program  might
 Manual page wine(1) line 1

```

---

### Post by aysiu on 2005-10-28
I'm not sure what to tell you. Hm. What about if you just Run the script without Running it in terminal?

---

### Post by eyebrowman92 on 2005-10-28
nothing happened. is there a way to install it with synaptic you could tell me?

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]nothing happened. is there a way to install it with synaptic you could tell me?[/QUOTE] I can assure you there's no way to install Internet Explorer through Synaptic. I wonder what the problem is...

---

### Post by eyebrowman92 on 2005-10-28
idk. i heard some people used winetools. could that be something because i dont have winetools downloaded.

---

### Post by pgferro on 2005-10-28
Ironically i have the same exact problem, exaclty at the same time .. !
Isn't this community awsome ?

Anyway same exact problem, run the script (sudo) and got the final OK but locate ie6 no results.
Tried to run it not as su, and got this error :

> chmod: cannot access `/home/pgferro/.ies4linux/base': No such file or directory
/home/pgferro/.ies4linux/base/drive_c/Windows/System//dcom98.inf: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//install.exe: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//eula98.txt: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//relnt98.txt: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//oleaut32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//secur32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//compobj.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//ole2.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//ole32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//olecnv32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//olethk32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcltc1.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcltc5.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcltccm.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpclts5.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcltscm.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcns4.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcrt4.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcss.exe: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//storage.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//stdole2.tlb: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//stdole32.tlb: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//imagehlp.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//dllhost.exe: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//comcat.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//iprop.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcmqcl.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//rpcmqsvr.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//olepro32.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//asycfilt.dll: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//ADVPACK.DLL: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//W95INF32.DLL: can't create file path
/home/pgferro/.ies4linux/base/drive_c/Windows/System//W95INF16.DLL: can't create file path
pgferro@pghome:~/ies4linux$ cd ./ies4linux
bash: cd: ./ies4linux: Not a directory


????

Thanks !

--
PG

---

### Post by eyebrowman92 on 2005-10-28
lol youre thanking me. do you know if you have winetools installed?

---

### Post by aysiu on 2005-10-28
I think I figured out the problem. You need to install cabextract. ```
sudo apt-get install cabextract
``` Then double-click on *ies4linux.sh* and Run in terminal.

---

### Post by eyebrowman92 on 2005-10-28
yes thank you so much you dont know how much i appreciate your help. one other thing i did this a week or so ago but i forgot how top there was a thing for downloading and installing opera web browser and multimedia codecs and other things. if you know what it is and how i cant get it please tell me. thanks again.

---

### Post by pgferro on 2005-10-28
well, in my case (and i'm writing from ie6 on ubumtu) the ie6 is in /home/pgferro/bin/
I accidentally reduce the firefox window and saw the shotcut on desktop !!!
Looking at properties there it is....

Try check it 

--
PG

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]yes thank you so much you dont know how much i appreciate your help.[/quote] Does that mean it worked? Please tell me if it did.

> one other thing i did this a week or so ago but i forgot how top there was a thing for downloading and installing opera web browser and multimedia codecs and other things. if you know what it is and how i cant get it please tell me. thanks again. Are you talking about Automatix? I don't know if that installs Opera. These two links may help:

[http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by aysiu on 2005-10-28
[QUOTE=pgferro]well, in my case (and i'm writing from ie6 on ubumtu) the ie6 is in /home/pgferro/bin/
I accidentally reduce the firefox window and saw the shotcut on desktop !!!
Looking at properties there it is....

Try check it 

--
PG[/QUOTE] So it ie6 working for you?

---

### Post by eyebrowman92 on 2005-10-28
asyiu, do you know of one specific program that downoads and installs opera, multimedia codecs and several other programs. i forget the name of it and what the code is for a terminal. please help me. thanks.

---

### Post by pgferro on 2005-10-28
Yes, it's working perfectly

---

### Post by aysiu on 2005-10-28
[QUOTE=eyebrowman92]asyiu, do you know of one specific program that downoads and installs opera, multimedia codecs and several other programs. i forget the name of it and what the code is for a terminal. please help me. thanks.[/QUOTE] See post #26 in this thread.

[quote=pgferro]Yes, it's working perfectly[/quote] Awesome.

---

### Post by eyebrowman92 on 2005-10-29
ok ive gotten as far as extracting the tar file to my desktop but now im stumped. what now?

---

### Post by aysiu on 2005-10-29
[QUOTE=eyebrowman92]ok ive gotten as far as extracting the tar file to my desktop but now im stumped. what now?[/QUOTE] 1. sudo apt-get update
2. sudo apt-get install wine cabextract
3. Open the newly extracted folder.
4. Double-click on ies4linux.sh
5. Run in terminal
6. ie6 will be in /home/username/bin/

---

### Post by clparker on 2005-10-29
I think the real problem here is why nobody is asking the important question like who the hell would want to run IE on a linux macheine? If you love IE use windows.

---

### Post by aysiu on 2005-10-29
[QUOTE=clparker]I think the real problem here is why nobody is asking the important question like who the hell would want to run IE on a linux macheine? If you love IE use windows.[/QUOTE] How about people who want to have access to IE-only websites? (Firefox's User Agent Switcher extension is wonderful, but it doesn't work 100% of the time.) How about web designers who want to know what their webpages will look like on the web browser the vast majority of internet users use? Think beyond your own needs. There are any number of reasons someone could need IE in Linux.

---

### Post by monkey89 on 2005-11-05
I wanted to clarify a little problem that some of you seem to be having -

locate uses a database.  The database should update automatically every night, but it isn't instantaneous when files change.  If you want to search for files that have just been updated or something like that, use a command like:

find -name ie6

It's working fine here with wine 0.9 from the winehq repositories.  It's in ~/bin/ie6 - I ran the script as a regular user.

---

### Post by barmaley on 2005-11-06
Hello, people

I have installed the latest ies4linux.
I did it because there are some programmers that don't know of exist&#1511;nce of any other browser except IE, therefore some sites can be viewed merely by the IE.
The IE works good, but, as usually, there are problems with it. For example, I needed to browse the site with e-maps of Israel written in Java (and of course neither Opera nor Firefox can view it correctly). So, can anybody try to view it with your IE and tell me if your were sucsessful, cause I wasn't and the system hung up: [http://www.e-map.co.il/index.asp](http://www.e-map.co.il/index.asp)

In windows it is displayed correctly, but to reboot just for it or any other IE-only sites is IMHO silly.
If you can resolve the problem, please, post the solution here.
Thank you in advance.

---

### Post by eyebrowman92 on 2005-11-06
im having the same problem. i think we needto download the java plug-in for the shockwave and flash players, but i cant figure out how in the ie4linux.

---

### Post by eyebrowman92 on 2005-11-08
does anyone know hoow to install these?

---

### Post by chunk on 2005-11-15
[QUOTE=clparker]I think the real problem here is why nobody is asking the important question like who the hell would want to run IE on a linux macheine? If you love IE use windows.[/QUOTE]

There is some software which won't install under wine without IE installed.

Specifically, I'm trying to install the "Ding" software from southwest airlines to get discounted airfairs. It is possible to retrieve the information without having the Ding software, but for that you need a user ID and as far as I know the only way to obtain a user ID is through the "Ding" installation process.

---

### Post by babygigi on 2005-11-16
Okay i have it downloaded but it wn't let me  install everytime it tells me that i'm not connected to internet and tell me to run it later... y??

---

### Post by darknuala on 2005-11-16
Crossover Office installs it flawlessly.
You can search for the ie6 full install.exe file.  Alot of sites have it, and that would solve alot of your problems.

---

### Post by pepolez on 2005-12-11
i was able to satisfy WINEs ie6 dependency with no problems using ies4linux:
[http://www.tatanka.com.br/ies4linux/en/instructions/](http://www.tatanka.com.br/ies4linux/en/instructions/)


one thing though, i did have to grab dcom98.exe from (in my case) /home/alex/winetools/sys/ and copy that to /home/alex/ies4linux/downloads/ (i had to create the new downloads directory). after installing cabextract and perfroming that copy, i had no probs

my one annoyance being that i have v fast internet (15mbit) and one of the files was coming in at 1.5mbit, opther then that, no problems :P

> 
alex@nibbler:~/ies4linux$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  cabextract
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.7kB of archives.
After unpacking 147kB of additional disk space will be used.
Get:1 [http://mirror.internode.on.net](http://mirror.internode.on.net) breezy/universe cabextract 1.1-1 [44.7kB]
Fetched 44.7kB in 0s (132kB/s)

Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 96965 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.1-1_i386.deb) ...
Setting up cabextract (1.1-1) ...
alex@nibbler:~/ies4linux$ mkdir downloads
alex@nibbler:~/ies4linux$ cp ../winetools/sys/dcom98.exe downloads/
alex@nibbler:~/ies4linux$ ./ies4linux
=================  IEs 4 Linux =================
Install IE6, IE5.5 and IE5 on Linux via Wine.
Credits: Sergio Lopes <slopes at gmail dot com>
Project page: [http://tatanka.com.br/ies4linux](http://tatanka.com.br/ies4linux)
See README file for more info

Installation options:
[1] Install IE6, IE5.5 and IE5
[2] Install only IE6
[3] Install only IE5.5
[4] Install only IE5.0
Please choose an option: 2

Downloading everything we need ...
--20:18:22--  [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
           => `/home/alex/.ies4linux/downloads/DCOM98.EXE'
Resolving download.microsoft.com... 64.154.128.221, 66.142.247.254, 65.59.235.62Connecting to download.microsoft.com|64.154.128.221|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,229,056 (1.2M) [application/octet-stream]

100%[====================================>] 1,229,056    914.74K/s

20:18:26 (913.14 KB/s) - `/home/alex/.ies4linux/downloads/DCOM98.EXE' saved [1229056/1229056]

--20:18:26--  [http://activex.microsoft.com/controls/vc/mfc40.cab](http://activex.microsoft.com/controls/vc/mfc40.cab)
           => `/home/alex/.ies4linux/downloads/mfc40.cab'
Resolving activex.microsoft.com... 207.46.249.55
Connecting to activex.microsoft.com|207.46.249.55|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 592,948 (579K) [application/octet-stream]

100%[====================================>] 592,948      191.93K/s    ETA 00:00

20:18:31 (191.64 KB/s) - `/home/alex/.ies4linux/downloads/mfc40.cab' saved [592948/592948]

--20:18:31--  [http://www.mirror.ac.uk/mirror/ftp.evolt.org/ie/32bit/6.0/ie60.exe](http://www.mirror.ac.uk/mirror/ftp.evolt.org/ie/32bit/6.0/ie60.exe)           => `/home/alex/.ies4linux/downloads/ie60.exe'
Resolving [www.mirror.ac.uk](www.mirror.ac.uk)... 194.80.135.25
Connecting to www.mirror.ac.uk|194.80.135.25|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.mirror.ac.uk/sites/ftp.evolt.org/ie/32bit/6.0/ie60.exe](http://download.mirror.ac.uk/sites/ftp.evolt.org/ie/32bit/6.0/ie60.exe) [following]
--20:18:41--  [http://download.mirror.ac.uk/sites/ftp.evolt.org/ie/32bit/6.0/ie60.exe](http://download.mirror.ac.uk/sites/ftp.evolt.org/ie/32bit/6.0/ie60.exe)
           => `/home/alex/.ies4linux/downloads/ie60.exe'
Resolving download.mirror.ac.uk... 194.80.135.25
Reusing existing connection to [www.mirror.ac.uk:80](www.mirror.ac.uk:80).
HTTP request sent, awaiting response... 200 OK
Length: 80,472,659 (77M) [application/octet-stream]

100%[====================================>] 80,472,659    74.52K/s    ETA 00:00

20:26:54 (160.13 KB/s) - `/home/alex/.ies4linux/downloads/ie60.exe' saved [80472659/80472659]

--20:26:55--  [http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab](http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab)
           => `/home/alex/.ies4linux/downloads/swflash.cab'
Resolving fpdownload.macromedia.com... 63.219.179.131, 63.219.179.143
Connecting to fpdownload.macromedia.com|63.219.179.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 741,237 (724K) [text/plain]

100%[====================================>] 741,237      213.88K/s    ETA 00:00

20:27:05 (213.48 KB/s) - `/home/alex/.ies4linux/downloads/swflash.cab' saved [741237/741237]

[ OK ]

Creating basic Windows installation ...
 Creating Wine Prefix
 Installing DCOM98
 Installing ActiveX MFC40
 Finalizing
[ OK ]

Installing IE 6 ...
 Extracting and copying IE files
 Configuring ie6
[ OK ]

Installing Flash Player 8 ...
 Preparing installation
 Installing flash on ie6
[ OK ]

IEs4Linux installations finished! ...
alex@nibbler:~/ies4linux$ 


---

### Post by Billyka on 2006-05-24
I have IE up and running but i need java  to view a page.
does any one now what i need to do / where to get java?

(ps i'm new to linux ):confused:

---

### Post by LORD_PoLvO on 2006-05-24
i was able to install it and it ran straight after the installation but i cant get figure out how to get it to run after that  ```
Welcome, daniel! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.

I'll ask you some questions now. Just answer y or n (default answer is the bold one)

IE 6 will be installed automatically.
Do you want to install IE 5.5 SP2 too? [ y | n ] n

And do you want to install IE 5.01 SP2? [ y | n ] n

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT PT HU RU NL SV
JA KO NO DA CN TW FI PL AR HE CS EL TR
Default is EN-US. Hit enter to keep it or choose a different one:


By default, I will install everything at /home/daniel/.ies4linux
I will also install Flash 8 plugin and create Desktop shortcuts.
Is that ok for you? (To configure advanced options type n) [ y | n ] y

All right! Let's start the installations...

Downloading everything we need
 DCOM98.EXE
--21:30:39--  http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE
           => `/home/daniel/.ies4linux/downloads/DCOM98.EXE'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,229,056 (1.2M) [application/octet-stream]

100%[====================================>] 1,229,056    406.46K/s

21:30:42 (405.36 KB/s) - `/home/daniel/.ies4linux/downloads/DCOM98.EXE' saved [1229056/1229056]

 mfc40.cab
--21:30:42--  http://activex.microsoft.com/controls/vc/mfc40.cab
           => `/home/daniel/.ies4linux/downloads/mfc40.cab'
Resolving activex.microsoft.com... 207.46.249.55
Connecting to activex.microsoft.com|207.46.249.55|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 592,948 (579K) [application/octet-stream]

100%[====================================>] 592,948      208.64K/s

21:30:45 (208.12 KB/s) - `/home/daniel/.ies4linux/downloads/mfc40.cab' saved [592948/592948]

 249973USA8.exe
--21:30:45--  http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe
           => `/home/daniel/.ies4linux/downloads/249973USA8.exe'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 838,328 (819K) [application/octet-stream]

100%[====================================>] 838,328      264.63K/s    ETA 00:00

21:30:49 (264.02 KB/s) - `/home/daniel/.ies4linux/downloads/249973USA8.exe' saved [838328/838328]

 ADVAUTH.CAB
--21:30:49--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ADVAUTH.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47,213 (46K) [application/octet-stream]

100%[====================================>] 47,213       300.33K/s

21:30:49 (300.03 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB' saved [47213/47213]

 CRLUPD.CAB
--21:30:49--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/CRLUPD.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,984 (13K) [application/octet-stream]

100%[====================================>] 12,984        --.--K/s

21:30:49 (197.78 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB' saved [12984/12984]

 IEDOM.CAB
--21:30:50--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IEDOM.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 110,162 (108K) [application/octet-stream]

100%[====================================>] 110,162      577.49K/s

21:30:50 (577.48 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB' saved [110162/110162]

 IE_S1.CAB
--21:30:50--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S1.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,525,813 (1.5M) [application/octet-stream]

100%[====================================>] 1,525,813    410.78K/s    ETA 00:00

21:30:54 (403.95 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB' saved [1525813/1525813]

 IE_S2.CAB
--21:30:54--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S2.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S2.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,458,213 (1.4M) [application/octet-stream]

100%[====================================>] 1,458,213    397.70K/s    ETA 00:00

21:30:58 (399.52 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S2.CAB' saved [1458213/1458213]

 IE_S5.CAB
--21:30:58--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S5.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S5.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,458,213 (1.4M) [application/octet-stream]

100%[====================================>] 1,458,213    414.30K/s    ETA 00:00

21:31:02 (404.72 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S5.CAB' saved [1458213/1458213]

 IE_S4.CAB
--21:31:02--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S4.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S4.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,458,213 (1.4M) [application/octet-stream]

100%[====================================>] 1,458,213    409.02K/s    ETA 00:00

21:31:11 (407.73 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S4.CAB' saved [1458213/1458213]

 IE_S3.CAB
--21:31:11--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S3.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S3.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,458,213 (1.4M) [application/octet-stream]

100%[====================================>] 1,458,213    406.66K/s    ETA 00:00

21:31:15 (405.43 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S3.CAB' saved [1458213/1458213]

 IE_S6.CAB
--21:31:15--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S6.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S6.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 258,071 (252K) [application/octet-stream]

100%[====================================>] 258,071      503.75K/s

21:31:15 (502.11 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/IE_S6.CAB' saved [258071/258071]

 SCR56EN.CAB
--21:31:16--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SCR56EN.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/SCR56EN.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 800,365 (782K) [application/octet-stream]

100%[====================================>] 800,365      422.75K/s

21:31:18 (421.37 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/SCR56EN.CAB' saved [800365/800365]

 SETUPW95.CAB
--21:31:18--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SETUPW95.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 928,786 (907K) [application/octet-stream]

100%[====================================>] 928,786      411.79K/s

21:31:20 (410.74 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB' saved [928786/928786]

 FONTCORE.CAB
--21:31:20--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTCORE.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/FONTCORE.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 762,249 (744K) [application/octet-stream]

100%[====================================>] 762,249      437.45K/s

21:31:22 (436.33 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/FONTCORE.CAB' saved [762249/762249]

 FONTSUP.CAB
--21:31:22--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTSUP.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/FONTSUP.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 643,814 (629K) [application/octet-stream]

100%[====================================>] 643,814      443.19K/s

21:31:24 (442.03 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/FONTSUP.CAB' saved [643814/643814]

 VGX.CAB
--21:31:24--  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/VGX.CAB
           => `/home/daniel/.ies4linux/downloads/ie6/EN-US/VGX.CAB'
Resolving download.microsoft.com... 210.8.175.253, 65.57.86.62
Connecting to download.microsoft.com|210.8.175.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,005,192 (982K) [application/octet-stream]

100%[====================================>] 1,005,192    412.89K/s

21:31:27 (411.39 KB/s) - `/home/daniel/.ies4linux/downloads/ie6/EN-US/VGX.CAB' saved [1005192/1005192]

 swflash.cab
--21:31:27--  http://download.macromedia.com/get/shockwave/cabs/flash/swflash.cab
           => `/home/daniel/.ies4linux/downloads/swflash.cab'
Resolving download.macromedia.com... 216.104.212.81
Connecting to download.macromedia.com|216.104.212.81|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 744,827 (727K) [text/plain]

100%[====================================>] 744,827      280.47K/s

21:31:30 (279.94 KB/s) - `/home/daniel/.ies4linux/downloads/swflash.cab' saved [744827/744827]

[ OK ]

Installing IE 6
 Initializing
 Creating Wine Prefix
 Extracting CAB files
 Installing IE 6
 Installing TTF Fonts
 Installing RICHED20
 Installing ActiveX MFC40
 Installing DCOM98
 Installing registry
 Finalizing
[ OK ]

Installing Flash Player 8
 Extracting files
 Processing inf file
 Installing flash on ie6
[ OK ]

IEs 4 Linux installations finished!

To run your IEs, type:
fixme:actctx:CreateActCtxW 0x7fb8fa70 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8f838
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:CreateActCtxW 0x7fb8f734 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8f4fc
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:ActivateActCtx (nil) 0x7fb8ed7c
fixme:actctx:CreateActCtxW 0x7fb8d360 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8d128
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dd28
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:actctx:CreateActCtxW 0x7fb8d204 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8cfcc
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dc80
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c072,0x00000001,0x7fb8dc90):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dd68
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dcdc
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dcb4
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dc68
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8d050
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8d050
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8d050
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8dc98
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10052, wParam=0x00000000, size.cx=1280, size.cy=1020 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10052,0x00008003,0x0c02b7ff,0x0000c072,0x00000001,0x7fb8dcd0):semi stub.
err:rebar:REBAR_Layout no redraw and client is zero, skip layout
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8de2c
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:CreateActCtxW 0x7fb8c654 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8c41c
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:CreateActCtxW 0x7fb8a870 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8a638
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8ba58
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:CreateActCtxW 0x7fb8654c 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb86314
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:shell:NTSHChangeNotifyRegister (0x10028,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x7fb8ea68):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:actctx:CreateActCtxW 0x7fb8b9c0 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8b788
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8e770
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8e724
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8e6dc
fixme:toolbar:TOOLBAR_CheckStyle [0x10072] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10072] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:shell:NTSHChangeNotifyRegister (0x10072,0x00008003,0x00008000,0x0000c072,0x00000001,0x7fb8e6ec):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10072, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10072] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8e6b0
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x7fb8e6c0
fixme:toolbar:TOOLBAR_CheckStyle [0x10076] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10076] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10076, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10076] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10076,0x00008003,0x0c02b7ff,0x0000c072,0x00000001,0x7fb8e6f4):semi stub.
fixme:shell:UnixFolder_IShellFolder2_GetUIObjectOf Unknown interface {00021500-0000-0000-c000-000000000046} in GetUIObjectOf
fixme:toolbar:TOOLBAR_CheckStyle [0x10076] TBSTYLE_REGISTERDROP not implemented
fixme:shell:DAD_ShowDragImage 0x00000000 stub
fixme:toolbar:TOOLBAR_CheckStyle [0x10072] TBSTYLE_REGISTERDROP not implemented
fixme:shell:DAD_ShowDragImage 0x00000000 stub
fixme:shell:DAD_ShowDragImage 0x00000001 stub
fixme:shell:DAD_ShowDragImage 0x00000000 stub
fixme:shell:DAD_ShowDragImage 0x00000001 stub
fixme:menu:TrackPopupMenuEx not fully implemented
fixme:menu:TrackPopupMenuEx not fully implemented
fixme:menu:TrackPopupMenuEx not fully implemented
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:shell:DAD_ShowDragImage 0x00000000 stub
fixme:shell:DAD_ShowDragImage 0x00000001 stub



```

---

### Post by LORD_PoLvO on 2006-05-24
wait i was able to navigate my way to the bin and there was ie6 file and i can just run it in terminal i have no idea y it would not run when i typed in ie6 lol

---

### Post by em3raldxiii on 2006-07-10
I'm having difficulty getting ActiveX to work correctly with ies4linux.  Any site I hit that scans for ActiveX tells me it's not correctly installed ... annoying as heck.  Anyone have any slick fixes?

---

