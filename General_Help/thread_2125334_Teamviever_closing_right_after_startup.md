---
title: "Teamviever closing right after startup"
date: 2013-03-13
forum: General Help
---

### Post by Tecco on 2013-03-13
I get this in the terminal window.
Init...
Checking setup...
Launching TeamViewer...
fixme:service:scmdatabase_autostart_services Auto-start service L"MountMgr" failed to start: 2
fixme:service:scmdatabase_autostart_services Auto-start service L"PlugPlay" failed to start: 2
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32d918,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32dc60,0x00000000), stub!
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:msg:ChangeWindowMessageFilter 233 00000001
fixme:msg:ChangeWindowMessageFilter 4a 00000001
fixme:msg:ChangeWindowMessageFilter 407 00000001
fixme:msg:ChangeWindowMessageFilter 49 00000001
fixme:bitmap:CreateBitmapIndirect planes = 0
fixme:bitmap:CreateBitmapIndirect planes = 0
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1005a 0x00000000
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000122-0000-0000-c000-000000000046}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {00000122-0000-0000-c000-000000000046}, 80040155
fixme:msg:ChangeWindowMessageFilter c04f 00000001
fixme:nls:GetGeoInfoW -1 4 0x32e1bc 3 0
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0
fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0
fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0
fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0
Terminated

Any help to fix the problem appreciated. :)

---

### Post by LynNicks on 2013-03-13
This has happened to me with a couple of applications. Try finding the .teamviewer folder in your home folder and clearing it's contents. (Don't worry, it won't uninstall the program)

---

### Post by Tecco on 2013-03-13
Hmm, there is no .teamviewer folder in the home folder(including hidden) :/
EDIT: Found it under config, tho clearing the folder didnt help :/ it fills in new files in the folder and same thing happens,terminates after startup :(

---

### Post by chris-a-dances on 2013-08-30
I am running into the same issue here and was wondering if you found a solution? I have deleted the .config/teamviewer files as well as re-installing teamviewer completely to no avail. I know that it had worked at least once before, but I can't get it to work now.

---

### Post by chris-a-dances on 2013-08-30
Actually the re-installation did fix the problem, I just needed to reboot my system.

---

