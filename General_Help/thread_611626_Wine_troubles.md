---
title: "Wine troubles"
date: 2007-11-13
forum: General Help
---

### Post by jjb123 on 2007-11-13
I installed wine a few days ago and tried to install steam, it installed fine but when I log in and it when I run it it says this it gives an error that says "Steam.exe (main exception): Win32 Structured Exception at 7BF3E65D: Attempt to read from virtual address 68 without appropriate access rights"

It also says the following in the console.
```

err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:ViewObject_SetAdvise (0x13afb378)->(1 00000002 0x148ca00)
fixme:shdocvw:PersistStreamInit_InitNew (0x13afb378)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x13afb378)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x13afb378)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1437ff80)->(1 00000002 0x148ca68)
fixme:shdocvw:PersistStreamInit_InitNew (0x1437ff80)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1437ff80)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1437ff80)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
err:ole:CoGetClassObject apartment not initialised
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7bbfd2b7, 0x7bbfd2b0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d218, 0x7bbfd2b0): stub
fixme:wininet:InternetLockRequestFile STUB
err:cabinet:FDICopy FDIIsCabinet failed.
err:mshtml:check_version Could not open VERSION file
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x13afb40c)->((null) 1 0x33bcac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 25 2 0x33bcc0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 26 2 0x33bcc0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x13afb40c)->(0x33bcfc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33bdb8 (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x1426bfb0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x142698e0)
fixme:mshtml:InternetBindInfo_GetBindString (0x1426bfb0)->(10 0x33a6d8 1 0x33a6ec)
fixme:urlmon:ObtainUserAgentString (0, 0x33a6f7, 0x33a6f0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14269d28, 0x33a6f0): stub
fixme:mshtml:BSCServiceProvider_QueryService (0x1426bfb0)->({79eac9d2-baf9-11ce-8c82-00aa004ba90b} {79eac9d2-baf9-11ce-8c82-00aa004ba90b} 0x14269a88)
fixme:mshtml:BSCServiceProvider_QueryService (0x1426bfb0)->({4f9f9fcb-e0f4-48eb-b7ab-fa2ea9365cb4} {4f9f9fcb-e0f4-48eb-b7ab-fa2ea9365cb4} 0x33a6e4)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1426bfb0)->(0x33a6f8 0x33a6f0 0)
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 29 2 0x33d590 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x13afb40c)
fixme:shdocvw:ClientSite_GetContainer (0x13afb40c)->(0x33d5b0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13afb40c)->(0xb7e8f109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 25 2 0x33d4e4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 26 2 0x33d4e4 (nil))
Shutting down. . .
300fixme:mshtml:HttpNegotiate_OnResponse (0x1426bfb0)->(200 L"HTTP/1.0 200 OK\r\nDate: Tue, 13 Nov 2007 11:25:02 GMT\r\nServer: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch7\r\nX-Powered-By: PHP/5.2.0-8+etch7\r\nContent-Type: text/html;charset=utf-8\r\nConnection: close\r\n\r\n" (null) 0x33b9c0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13afb40c)->((null) 28 2 0x33c394 (nil))
client callback thread error
client callback thread error
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

I am using Kubuntu, 7.10 and wine 0.9.46.

Any help would be greatly appreciated. Thanks :).

---

### Post by jfinkels on 2007-11-13
You may want to try upgrading to the most recent version of wine. See here for more info [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by jjb123 on 2007-11-15
Ok, I don't know what I did but it seems to work now, thanks.

---

