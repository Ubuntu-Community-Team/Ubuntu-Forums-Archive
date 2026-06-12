---
title: "Running IE6 in Wine"
date: 2005-09-13
forum: General Help
---

### Post by Steve Smith on 2005-09-13
I'm trying to use Winetools to get IE up and running with Wine.

Althought it seems to be working now, after much-a-do, althought many times throug setting it up I get:

"Can't export. Registry key...", for example, one logfile reads:

"regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!

Success"

What do I need to change to allow it to access the (fake) registry, and does it really matter that it can't?

---

### Post by skoal on 2005-09-13
I got IE6 running quite well with Wine.  However, I used this procedure (which gave me no such errors): 

[http://www.ubuntuforums.org/showthread.php?t=58644&highlight=wine+ie6](http://www.ubuntuforums.org/showthread.php?t=58644&highlight=wine+ie6)

* Make sure to use the Sidenet installer and drop dcom98 in that same folder,

Ahh, Internet Explorer in linux.  Who'd a thunk it?  That's like mowing the front lawn with a rolling blade type pusher, as the John Deere sits quietly in the garage all gassed up and ready to roll...

\\//_

---

### Post by az on 2005-09-13
I used winetools and found that I needed wine-utils for it to work.  It is not mentioned in the dependancies.

---

### Post by Steve Smith on 2005-09-13
[QUOTE=skoal]* Make sure to use the Sidenet installer and drop dcom98 in that same folder,[/QUOTE]
Ah, I tried Sidenet first, but at that point  I didn't have dcom98, I'll give that a go, thanks!

[QUOTE=skoal]That's like mowing the front lawn with a rolling blade type pusher...[/QUOTE]
Even just making a website for a bunch of friends needs testing with Microsoft lawnmowers...

[QUOTE=azz]I used winetools and found that I needed wine-utils for it to work.  It is not mentioned in the dependancies.[/QUOTE]
Thanks, tho I've got wine-utils already.

---

### Post by Steve Smith on 2005-09-16
By dcom, do you mean dcom98.exe, and just placing it in the directory containing the sidenet setup file?  If so, that's what I've just done.

Here's what happened when I just tried sidenet, any suggestions welcome... :)

During setting up ie, a window popped up saying:
```
UpdCrl

AddCRL failed=>0x80090017 (-2146893801)
```
It carried on, here's the logfile:
```
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x7e050000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x7e050000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7e050074 
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:vcpUICallbackProc16 (0x3b80, 0705, 0000, 00000000, 77c8efbc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0x3b80, 070f, 0000, 00000000, 77c8efbc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0x3b80, 0710, 0000, 00000000, 77c8efbc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0x3b80, 070b, 0000, 00000000, 77c8efbc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0x3b80, 070c, 0000, 00000000, 77c8efbc) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:dc:GetLayout (0x7c0): stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x7d550000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x7d550000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7d550074 
fixme:shell:Stream_WriteLocationInfo writing empty location info
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:cabinet:process_files (basecab == ^0x783b0d18): Memory leak.
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\msdownld.tmp\\AS01DB86.tmp\\w95inf16.dll"
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\autokill.inf"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\autokill.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\ie4olrdr.map"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\advpack.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Bindlist.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Softboot.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Bindlist.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Softboot.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\ierunonce.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\ierunonce.err"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\npstub.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\egg.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\dskwmark.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\tck.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\wmark.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\userexbg.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\userexp.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\compon.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Web\\desktop.htx"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\setup\\ie4.inf"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\PROG~FBU\\ie40.cif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\PROG~FBU\\ie4.txt"
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\inf\\ie5dom.inf"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:rundll32:main Unable to find the entry point L"DelNodeRunDLL32C:\\\\Program" in L"advpack.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\Mobile Option Pack.dat"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\Mobile Option Pack.ini"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\IE5EXTRA.dat"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\IE5EXTRA.ini"
err:setupapi:SetupDefaultQueueCallbackA delete error 5 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\IE5BAKEX.dat"
err:setupapi:SetupDefaultQueueCallbackA delete error 5 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\IE5BAKEX.ini"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\Uninstall Information\\w2kexcp.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\\\Program Files\\Internet Explorer\\ie4regun"
fixme:dialog:MSGBOX_OnInit task modal msgbox ! Not modal yet.
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0401\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0403\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0404\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0405\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0406\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0407\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0408\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0409\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\040B\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\040C\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\040D\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\040E\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0410\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0412\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0413\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0414\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0415\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0416\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0419\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\041B\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\041D\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\041F\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0424\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\042D\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0804\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0816\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\040A\\hhctrlui.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\system\\mui\\0411\\hhctrlui.dll"
Microsoft (R) Cabinet Extraction Tool - Version (32G) 4.11.0610.0 (03/31/99)

Copyright (c) Microsoft Corp 1994-1999. All rights reserved.



 Cabinet mui.cab



Extracting c:\windows\system\mui\0401\hhctrlui.dll

Extracting c:\windows\system\mui\0403\hhctrlui.dll

Extracting c:\windows\system\mui\0404\hhctrlui.dll

Extracting c:\windows\system\mui\0405\hhctrlui.dll

Extracting c:\windows\system\mui\0406\hhctrlui.dll

Extracting c:\windows\system\mui\0407\hhctrlui.dll

Extracting c:\windows\system\mui\0408\hhctrlui.dll

Extracting c:\windows\system\mui\0409\hhctrlui.dll

Extracting c:\windows\system\mui\040B\hhctrlui.dll

Extracting c:\windows\system\mui\040C\hhctrlui.dll

Extracting c:\windows\system\mui\040D\hhctrlui.dll

Extracting c:\windows\system\mui\040E\hhctrlui.dll

Extracting c:\windows\system\mui\0410\hhctrlui.dll

Extracting c:\windows\system\mui\0412\hhctrlui.dll

Extracting c:\windows\system\mui\0413\hhctrlui.dll

Extracting c:\windows\system\mui\0414\hhctrlui.dll

Extracting c:\windows\system\mui\0415\hhctrlui.dll

Extracting c:\windows\system\mui\0416\hhctrlui.dll

Extracting c:\windows\system\mui\0419\hhctrlui.dll

Extracting c:\windows\system\mui\041B\hhctrlui.dll

Extracting c:\windows\system\mui\041D\hhctrlui.dll

Extracting c:\windows\system\mui\041F\hhctrlui.dll

Extracting c:\windows\system\mui\0424\hhctrlui.dll

Extracting c:\windows\system\mui\042D\hhctrlui.dll

Extracting c:\windows\system\mui\0804\hhctrlui.dll

Extracting c:\windows\system\mui\0816\hhctrlui.dll

Extracting c:\windows\system\mui\040A\hhctrlui.dll

Extracting c:\windows\system\mui\0411\hhctrlui.dll

err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwconn1.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwconn2.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\inetwiz.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\isignup.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwdl.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwx25a.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwx25b.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwx25c.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\icwip.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\phone.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\state.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\msicw.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\msn.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\Program Files\\ICW-Internet Connection Wizard\\support.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwconn1.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwconn2.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\inetwiz.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\isignup.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwdl.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwx25a.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwx25b.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwx25c.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\icwip.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\phone.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\state.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\msicw.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\msn.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\support.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\cns.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\nocns.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\progress.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\sidebar.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\connwiz.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\cwizfram.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\INTE~H1A\\Connection Wizard\\cwizintr.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwconn1.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwconn2.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\inetwiz.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\isignup.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwdl.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwx25a.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwx25b.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwx25c.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwip.dun"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\phone.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\state.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\msicw.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\msn.isp"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\sbscfg.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\support.icw"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\readme.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Connection Wizard\\icwread.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Start Menu\\Programs\\Accessories\\Internet Tools\\Internet Setup Wizard.lnk"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Start Menu\\Programs\\Accessories\\Internet Tools\\Get on the Internet.lnk"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Start Menu\\Programs\\Internet Explorer\\Connection Wizard.lnk"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Start Menu\\Programs\\Accessories\\Internet Tools\\Internet Connection Wizard.lnk"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\All Users\\Desktop\\Connect to the Internet.lnk"
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:vcpUICallbackProc16 (0xbb80, 0705, 0000, 00000000, 77c2083c) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xbb80, 070f, 0000, 00000000, 77c2083c) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xbb80, 0710, 0000, 00000000, 77c2083c) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xbb80, 070b, 0000, 00000000, 77c2083c) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xbb80, 070c, 0000, 00000000, 77c2083c) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:create_system_dirid unknown dirid 13
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
```
IE works, though it seems quite slow, and I can't access google.  Did I read somewhere that's because dcom isn't set up properly?

---

### Post by skoal on 2005-09-16
Happy, yes.  Go [here](http://www.microsoft.com/downloads/details.aspx?familyid=08b1ac1b-7a11-43e8-b59d-0867f9bdda66&displaylang=en) for dcom98.  Read the eula, download it, and place it in your sidenet path, like this:
```
skoal@morpheus:///tmp/wine-config-sidenet $ ls
COPYING     iebatch    readme.en      rosexplorer  true
[COLOR=DarkRed]dcom98.exe[/COLOR]  inf        readme.ja.euc  setup        wineconfig
fonts       readme.br  reg            shelllink    wineshelllink.ja
```
* notice that I actually 'mv'd that file to all lowercase letters...

*Make sure you install the wine version provided in that original link I gave you*.

Then, just run ./setup from the "sidenet" path above.  Choose option "2" from the sidenet setup and it should download IE6+WMV and create your ~/.wine path properly.  I'm no wine debugging guru so that info you posted above is ancient sea scroll text to me.  However, the quickest easiest way to ensure everything gets setup properly is to use a fresh ~/.wine path.  Backup your original to (say) ~/.wine~ and let sidenet go through the entire install, configuring wine along the way...

\\//_

---

### Post by Steve Smith on 2005-09-18
Thanks, dcom98's on now!  But it's still as slow, and some sites (such at this forum) won't load at all.  Any chance you could set your ie homepage to google & time how long it takes to launch ie and load the page?  Mine takes 17 seconds.

**Edit:** got rid of the lot and started again, down to 8 seconds now, which sounds almost reasonable.  This forum now works, but *some* of the images are missing, including the big Ubuntu logo.  Any ideas?

---

### Post by skoal on 2005-09-18
oops.  I had actually deleted all my wine stuff a few days ago since I only needed IE6 for msnbc.com, but I couldn't get the videos to work.

I do not remember google taking that long to fire up ( < 5 secs I believe, or the reasonable 8 which you cited).  I never did test IE6 on these forums, but if any images dont render properly maybe it's because they are in .png format?  I dunno.  Maybe it's a setting in IE6 itself and how it handles images (in general).  If you launch IE6 in a terminal, maybe wine debug output can offer a clue.

\\//_

---

### Post by Steve Smith on 2005-09-19
I'm onto the crossover office demo now, and it works a treat!  Images are there, so you're right, must have just been a setting somewhere.  Now the question is, is it worth me paying about £22 for someone else to deal with wine for me...  if it works as well with Dreamweaver...

---

### Post by skoal on 2005-09-19
[QUOTE=happysteve][...] is it worth me paying about £22 for someone else to deal with wine for me...[/QUOTE]
If crossover works great with most IE only sites and media plugins are a snap, then I'd say yes.  In fact, if you could try out the msnbc.com videos for me and see if they work, then I would happily plop down ~$30 myself for such a treat.

\\//_

---

### Post by Steve Smith on 2005-09-20
[QUOTE=skoal]if you could try out the msnbc.com videos for me and see if they work[/QUOTE]

Sure, will do, but I'm going for a reformat tonight, screwed a couple of things up.  I'll try it later in the week.  If I don't repost here in a few days, post in this thread to remind me!

---

