---
title: "Wine isn't working in Gutsy"
date: 2007-10-16
forum: General Help
---

### Post by Tlon on 2007-10-16
As shown, I'm having problems getting Wine to work in Gutsy.  I'm NOT getting error messages (I *did* look over the suggested threads).  I'm not getting anything, which is the problem.  When I try to run a Windows executable using wine, nothing happens.  When I try to do so from a terminal, here is the output:

m@E:~$ wine iexplore.exe
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cfdb9f8, overlapped 0x7cfdb9dc): stub
err:mshtml:set_profile SetCurrentProfile failed: 80520015
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x125194)->((null) 1 0x33fa7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 25 2 0x33fa90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fa90 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x125194)->(0x33facc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fb88 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1276e0)->(L"" L"" 0 0x33fbbc)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1276e0)->(0x33fbc0 0x33fbd0)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0xebed20)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0xebf2c0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 29 2 0x33fcb0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x125194)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 28 2 0x33fc08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x125194)->(0x33fb9c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x125194)->(0xb7e5c109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 25 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 21 2 (nil) (nil))

Any help would be dandy.

---

### Post by mosaic2s on 2007-11-25
when i click on wine configuration from menu, the system hangs. using gutsy on amd 64 bit.

---

### Post by nikoPSK on 2007-11-26
> **Tlon said:**
> As shown, I'm having problems getting Wine to work in Gutsy.  I'm NOT getting error messages (I *did* look over the suggested threads).  I'm not getting anything, which is the problem.  When I try to run a Windows executable using wine, nothing happens.  When I try to do so from a terminal, here is the output:

m@E:~$ wine iexplore.exe
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cfdb9f8, overlapped 0x7cfdb9dc): stub
err:mshtml:set_profile SetCurrentProfile failed: 80520015
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x125194)->((null) 1 0x33fa7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 25 2 0x33fa90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fa90 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x125194)->(0x33facc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fb88 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1276e0)->(L"" L"" 0 0x33fbbc)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1276e0)->(0x33fbc0 0x33fbd0)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0xebed20)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0xebf2c0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 29 2 0x33fcb0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x125194)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 28 2 0x33fc08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x125194)->(0x33fb9c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x125194)->(0xb7e5c109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 25 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 26 2 0x33fad0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x125194)->((null) 21 2 (nil) (nil))

Any help would be dandy.

what ver. wine?

---

