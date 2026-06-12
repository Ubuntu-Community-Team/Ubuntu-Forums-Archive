---
title: "Hardware Acceleration"
date: 2008-05-02
forum: General Help
---

### Post by Jookia on 2008-05-02
I can run a game using no hardware acceleration.. Problem is, it'll open up the game, but the graphics itself won't show. So how could I get Hardware mode working on the game?

Game is byond by the way. Also, I've managed to get it 'starting' by disabling desktop effects. But I get THIS..

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecf4,0x00000000), stub!
fixme:d3d:IWineD3DSwapChainImpl_Present Unhandled present options (nil)/0x32f1b0
fixme:richedit:ME_UpdateScrollBar ME_UpdateScrollBar had to call ME_WrapMarkedParagraphs
fixme:richedit:ME_UpdateScrollBar ME_UpdateScrollBar had to call ME_WrapMarkedParagraphs
fixme:richedit:ME_UpdateScrollBar ME_UpdateScrollBar had to call ME_WrapMarkedParagraphs
fixme:richedit:ME_UpdateScrollBar ME_UpdateScrollBar had to call ME_WrapMarkedParagraphs
fixme:shdocvw:PersistMemory_Load (0x1608c0)->(0x10139894 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x1608c0)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1608c0)->(0)
fixme:d3d:IWineD3DSwapChainImpl_Present Unhandled present options (nil)/0x32f314
fixme:shdocvw:PersistMemory_Load (0x141b58)->(0x10139894 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x141b58)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x141b58)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f408:2; TargetFrameName 0x32f418:0)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c314a08, overlapped 0x7c3149ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x151ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x141bf4)->((null) 1 0x32c744 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->((null) 25 2 0x32c758 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->((null) 26 2 0x32c758 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x141bf4)->(0x32c794)
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c858 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c8e8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:PersistMemory_Load (0x160c648)->(0x10139894 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x160c648)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x160c648)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f374:2; TargetFrameName 0x32f384:0)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x160c6e4)->((null) 1 0x32c6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x160c6e4)->((null) 25 2 0x32c6c4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x160c6e4)->((null) 26 2 0x32c6c4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x160c6e4)->(0x32c700)
fixme:shdocvw:ClOleCommandTarget_Exec (0x160c6e4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c7c4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x160c6e4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c854)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->((null) 29 2 0x32f148 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x141bf4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x160c6e4)->((null) 29 2 0x32f148 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x160c6e4)
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClientSite_GetContainer (0x141bf4)->(0x32ef60)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x141bf4)->(0xb7ebd725)
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->((null) 25 2 0x32ee94 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141bf4)->((null) 26 2 0x32ee94 (nil))
fixme:mshtml:HTMLDocument_QueryInterface (0x976ff0)->({d30c1661-cdaf-11d0-8a3e-00c04fc9e26e} 0x32ee18) interface not supported
wine: Unhandled page fault on read access to 0x00000000 at address 0x1005ad9a (thread 0046), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x1005ad9a).
```

---

### Post by rubicon on 2008-05-02
Can you find your game on [http://appdb.winehq.org/](http://appdb.winehq.org/) ?
There may be some notes on running it properly.

---

### Post by Jookia on 2008-05-02
Tried that.

---

