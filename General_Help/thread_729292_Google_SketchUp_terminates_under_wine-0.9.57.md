---
title: "Google SketchUp terminates under wine-0.9.57"
date: 2008-03-19
forum: General Help
---

### Post by rakydude on 2008-03-19
I'm having some problems running **Google SketchUp 6**. (I doesn't get version 5 to work either)
I'm using **wine-0.9.57** on **Kubuntu 7.10**


My first problem (witch i solved) was an error message saying "ChoosePixelFormat failed" followed by the program terminating when clicking OK. This was fixed by making a change in the regestry as suggested on [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=19720&sAllBugs](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=19720&sAllBugs)
```
regedit://HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK = 1
```

Now, however, the program crashes after loading some of the GUI (a few windows, file menus, and toolbars. I can clearly see the "Choose your settings"-window, and another window loads which I can't see what is before the program crashes.)

Here is my terminal output:
```

$ wine SketchUp.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_RETRIES: STUB
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:shdocvw:PersistStreamInit_InitNew (0x20838d0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x34d04c:3; TargetFrameName 0x34d03c:8)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x7bbfe9c8, overlapped 0x7bbfe9ac): stub
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x208396c)->((null) 1 0x34b348 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 25 2 0x34b370 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 26 2 0x34b370 (nil))
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x208396c)->(0x34b3bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34b4d0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34b540)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_SetContentType default action not implemented
fixme:shdocvw:PersistStreamInit_InitNew (0x2084ce8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x34b190:3; TargetFrameName 0x34b180:8)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:navigate_url Unsupported args (Flags 0x34b928:3; TargetFrameName 0x34b918:8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x34b880:3; TargetFrameName 0x34b870:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 29 2 0x34d5cc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x208396c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34d4ec)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34d4ec)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34d4ec)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClientSite_GetContainer (0x208396c)->(0x34d56c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x208396c)->(0xb7e08b74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 25 2 0x34d480 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 26 2 0x34d480 (nil))
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x2084d84)->((null) 1 0x34bce8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 25 2 0x34bd10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 26 2 0x34bd10 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x2084d84)->(0x34bd5c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34be70 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34bee0)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:HlinkTarget_SetBrowseContext (0x266bcc8)->((nil))
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x2084d84)->((null) 1 0x34bce8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 25 2 0x34bd10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 26 2 0x34bd10 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x2084d84)->(0x34bd5c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34be70 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34bee0)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:mshtml:nsChannel_SetContentType default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 29 2 0x34d5cc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x2084d84)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34d4ec)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34d4ec)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClientSite_GetContainer (0x2084d84)->(0x34d56c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x2084d84)->(0xb7e08b74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 25 2 0x34d480 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 26 2 0x34d480 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x2084d84)->(0x34d56c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x2084d84)->(0xb7e08b74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 25 2 0x34d480 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 26 2 0x34d480 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({000214d1-0000-0000-c000-000000000046} 67 0 0x34b34c 0x34b33c)
fixme:hlink:IHlink_fnSetMonikerReference (0x2d16eb8)->(0 0x2e3d318 (null))
fixme:hlink:IHlink_fnGetStringReference (0x2d16eb8) -> (1 (nil) 0x34b1c8)
fixme:shdocvw:navigate_bsc Navigation canceled
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 26 2 0x34d5bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 29 2 0x34d5cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x208396c)->(0x7bc9f9d4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x208396c)->((null) 28 2 0x34d4fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 26 2 0x34d5bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 29 2 0x34d5cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x2084d84)->(0x7bc9fa03)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2084d84)->((null) 28 2 0x34d4fc (nil))
DRM_I830_CMDBUFFER: -22

```

It is suggested in the forum I linked to, to change the following registry keys
```

[HKEY_CURRENT_USER\Software\Google\SketchUp6\Google SketchUp TOTD]
"HelpPage"="0"
"ShowOnStartUp"="\"false\"" 

```
But the registry folder "*HKEY_CURRENT_USER\Software\Google\SketchUp6\Google SketchUp TOTD*" does not exist on my Sketchup installation.

Does anyone have any suggestions on how to solve this?
I'm not using any XGL or Compiz.

---

### Post by rakydude on 2008-03-20
Help please? :)

---

### Post by rakydude on 2008-03-21
Bump

---

