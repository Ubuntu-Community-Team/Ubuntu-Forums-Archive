---
title: "[SOLVED] Wow and Wine"
date: 2008-06-07
forum: General Help
---

### Post by floyin on 2008-06-07
I cant get wow to start. i get this

```
spiriten@spiriten-desktop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x12fda8)->(0x32e6fc)
fixme:shdocvw:OleControl_FreezeEvents (0x12fda8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12fda8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x1303b0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130390): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130390): WIN32_FIND_DATA is not yet filled.
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:iphlpapi:NotifyAddrChange (Handle 0x7db1da08, overlapped 0x7db1d9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x125ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12fe44)->((null) 1 0x32bfa8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 25 2 0x32bfbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 26 2 0x32bfbc (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12fe44)->(0x32bff8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c0bc (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x131fb0)->(L"" L"" 0 0x32c0f4)
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 29 2 0x32ecd0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12fe44)
fixme:shdocvw:ClientSite_GetContainer (0x12fe44)->(0x32eb14)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12fe44)->(0xf7dd0759)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 25 2 0x32ea48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 26 2 0x32ea48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fe44)->((null) 28 2 0x32ec6c (nil))
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12fda8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x147458)->((nil))
fixme:shdocvw:OleObject_Close (0x12fda8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
spiriten@spiriten-desktop:~$ Error: API mismatch: the NVIDIA kernel module has version 169.12,
but this NVIDIA driver component has version 96.43.05.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d610000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d610000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
Error: API mismatch: the NVIDIA kernel module has version 169.12,
but this NVIDIA driver component has version 96.43.05.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ece0,0x00000000), stub!
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


```

Anyone able to help? This happens when i start wow with wine. Wow crashes at the same time. Ive been messing with this all night and have been all over google.

---

### Post by floyin on 2008-06-07
Sorry for double post, but i found that if installed wow from the CD's this fixed the problem. My Nvdia drivers crashed once before while restarting. This may have also done it. Now im patching =D

---

### Post by rraj.be on 2008-06-07
Not all windows programs are capable of running using the wine due to many reasons including driver support DLL issues etc.

Hence first check whether your program is compatible with wine in their home page,or here.

```
[http://www.codeweavers.com/compatibility/]("http://www.codeweavers.com/compatibility/")
```

Further than trying to install windows application inside ubuntu you can get a package similar in use of that like your windows program.

All we need is what program's you need.

Just specify the application and we can suggest you some package's.

---

### Post by floyin on 2008-06-07
World of Warcraft is compatible with wine, thats how i found out about wine. Its updating now, so it should be good to go here in a few minutes

---

### Post by rraj.be on 2008-06-07
Don't forget to mark your thread as solved if it's solved.

Look at my signature for more info.

---

### Post by floyin on 2008-06-07
The problem is no longer solved, unfortunately. When i run it from terminal here is what i get:
```
spiriten@spiriten-desktop:~$ env WINEPREFIX="/home/spiriten/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x1304a8)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x1304a8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1304a8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x130a38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130a18): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130a18): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1313b0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1313b0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1313b0): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d90ba08, overlapped 0x7d90b9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x130544)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x130544)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1313b0)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x130544)
fixme:shdocvw:ClientSite_GetContainer (0x130544)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x130544)->(0xf7e7f759)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 26 2 0x32e780 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130544)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1304a8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1497a0)->((nil))
fixme:shdocvw:OleObject_Close (0x1304a8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
spiriten@spiriten-desktop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7d490000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d490000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


```

I would love to get this fixed.

---

### Post by floyin on 2008-06-07
Sorry again but it is finally solved. The error was in the RunOnce.wtf where it never set to openGL. If anyone has problems like I did, copy what is in your config.wtf to your RunOnce.wtf

---

### Post by madhead on 2008-09-24
Where are these files located? I am trying to get the trail download working


Cheers,

---

### Post by Cyanide Cloud on 2008-09-24
i love how the extention is .wtf  lol

---

