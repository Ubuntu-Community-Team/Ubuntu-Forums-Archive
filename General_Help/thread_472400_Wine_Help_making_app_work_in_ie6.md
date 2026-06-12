---
title: "Wine Help making app work in ie6"
date: 2007-06-13
forum: General Help
---

### Post by Freaky_Llama on 2007-06-13
So, I got IE6 to work and now I'm very anxious to get an app to run under it. The app uses activeX as far as I know, possibly another technology. 

The app is Clarify, which is a Help Desk ticketing software. Its a complete Webapp right now, with a move to an Oracle Desktop app later.

I got the ActiveX control to work, which loads a login screen. After it loads, it shows the complete interface with my user details (basically the top of a tree of my queues). 

The issue here is, even though the mouseover seems to 'highlight' the buttons, clicking them doesn't actually do anything. Its like they're all dead buttons. 

I've copied over mfc40.dll, mfc42.dll, and shell32.dll from a WindowsXP machine running IE6 to the Wine system32 folder. 

I'd greatly appreciate anyone help with suggestions on what to try.

---

### Post by cookies on 2007-06-13
How'd you install IE6, with IES4Linux, if you did, we have some set up to do. *Fun fun*

---

### Post by Freaky_Llama on 2007-06-13
Yeah, it was with IEs4Linux. I tried doing it directly in Wine, but after the Gecko thing installed, it stopped working. So then I reran the IEs4Linux script.

What is this "setup"? If somebody wants to answer it, please do so. I'm gonna go looking for a tutorial as well.

I couldn't find anything off hand that would benefit me.

---

### Post by cookies on 2007-06-13
> **Freaky_Llama said:**
> Yeah, it was with IEs4Linux. I tried doing it directly in Wine, but after the Gecko thing installed, it stopped working. So then I reran the IEs4Linux script.

What is this "setup"? If somebody wants to answer it, please do so. I'm gonna go looking for a tutorial as well.

I couldn't find anything off hand that would benefit me.

The setup is making the wineprefix.

WINEPREFIX="/home/NAME/.ies4linux/ie6" wineprefixcreate 

NAME = Your user name

WINEPREFIX="/home/NAME/.ies4linux/ie6" wine winecfg

Okay, now drop your DLLs to

/home/NAME/.ies4linux/ie6/drive_c/windows/system32

And overwrite them if they are there.

Now in winecfg, select default settings then go to Libraries, and enter all the DDL's you just put in to system32 (Just the new ones you put in) and set them to Native.

That'll get the DLL's set up.

---

### Post by Freaky_Llama on 2007-06-13
Thank you for that. I went through it step by step, unfortunately, it didn't help the situation.

I still have the same symptoms and I even moved the new dll's distributed with the webapp and it din't help.

Here's the output of ie6 from time of open until time of close.

```
fixme:actctx:ActivateActCtx 0x1648c0 0x33f8d8
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:shell:ReadCabinetState Initializing shell cabinet settings
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c075,0x00000001,0x33daa0):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x1003a wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:dpa:DPA_LoadStream phDpa=0x33d4dc loadProc=0xbaba1c pStream=0x188420 lParam=1817b0
fixme:dpa:DPA_LoadStream dwSize=0 dwData2=0 dwItems=0
fixme:dpa:DPA_LoadStream new hDpa=0x181778, errorcode=80004005
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10050, wParam=0x00000000, size.cx=1280, size.cy=796 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10050,0x00008003,0x0c02b7ff,0x0000c075,0x00000001,0x33dae0):semi stub.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:NTSHChangeNotifyRegister (0x10028,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x33ea88):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:win:GetProcessDefaultLayout ( 0x33d1d4 ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33d1d4 ): No BiDi
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:ras:RasEnumConnectionsW (0x196398,0x78d9d918,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:ras:RasEnumEntriesW ((nil),(null),0x1fd908,0x78d9d5e0,0x1fd5f4),stub!
fixme:winsock:WSALookupServiceBeginW (0x78c8c990 0x00000210 0x78c8c9f0) Stub!
fixme:ras:RasEnumConnectionsW (0x196398,0x78c8c508,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:win:GetProcessDefaultLayout ( 0x33e630 ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33e630 ): No BiDi
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:shell:ExtractAssociatedIconExW 0x71160000 L"shell32.dll" 0x33ddc8 0x33ddc8): stub
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:shell:ExtractAssociatedIconExW 0x71160000 L"shell32.dll" 0x33ddc8 0x33ddc8): stub
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
err:shell:SHCoCreateInstance LoadFromShell failed for CLSID=
        {a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 4 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 4 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 5 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 5 is not valid, number of bitmaps in imagelist: 4
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 4 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 4 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 5 is not valid, number of bitmaps in imagelist: 4
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 5 is not valid, number of bitmaps in imagelist: 4
fixme:hook:IsWinEventHookInstalled (32773)-stub!

fixme:win:GetProcessDefaultLayout ( 0x33ea9c ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33ea9c ): No BiDi
fixme:shell:SHFlushClipboard stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```


Edit:

Hmmm, actually, I just realized that when I do the first step, It drops me to a wine-dbg prompt
```
fixme:actctx:ActivateActCtx 0x1b9100 0x33cfdc
fixme:actctx:DeactivateActCtx 00000000 00f00bad
wine: Unhandled page fault on read access to 0x8000010c at address 0x701069b2 (thread 0012), starting debugger...
WineDbg starting on pid 0011
Unhandled exception: page fault on read access to 0x8000010c in 32-bit code (0x701069b2).
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file rpcrt4.dbg ("\x01")
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:701069b2 ESP:0034fcb8 EBP:0034fcf8 EFLAGS:00210282(   - 00      - RIS1)
 EAX:00000011 EBX:00000000 ECX:800000f8 EDX:00000000
 ESI:800000f8 EDI:00000000
Stack dump:
0x0034fcb8:  00000060 701067e6 00000000 70101dc3
0x0034fcc8:  00110ab8 00000001 7bc7c4b8 00000000
0x0034fcd8:  00000060 0034fcf8 0034fcc8 0034f82c
0x0034fce8:  0034ff2c 7010a6dc 70146488 ffffffff
0x0034fcf8:  0034fd18 7bc39485 70100000 00000001
0x0034fd08:  00000001 7eb62820 7eab0000 7bc7c4b8
Backtrace:
=>1 0x701069b2 in rpcrt4 (+0x69b2) (0x0034fcf8)
  2 0x7bc39485 call_dll_entry_point+0x15() in ntdll (0x0034fd18)
  3 0x7bc3ae0d in ntdll (+0x2ae0d) (0x0034fda8)
  4 0x7bc3b41d in ntdll (+0x2b41d) (0x0034fde8)
  5 0x7bc3b362 in ntdll (+0x2b362) (0x0034fe28)
  6 0x7bc3b362 in ntdll (+0x2b362) (0x0034fe68)
  7 0x7bc3b362 in ntdll (+0x2b362) (0x0034fea8)
  8 0x7bc3d8ae LdrInitializeThunk+0x2be() in ntdll (0x0034ff08)
  9 0x7b874dca in kernel32 (+0x54dca) (0x0034ffe8)
  10 0xb7e82af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x701069b2: cmpl        0x14(%esi),%eax
Wine-dbg>
```

---

