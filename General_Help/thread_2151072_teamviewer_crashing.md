---
title: "teamviewer crashing"
date: 2013-06-03
forum: General Help
---

### Post by podgorsek on 2013-06-03
Hey guys, I'd really need your help. There is no way I can start a teamviewer on my ubuntu 12 04. Each time, I start it up, it starts for about 5sec and then crashes :/ someone please help me.
Here is a terminal log:

[FONT=arial]root@Ubuntu-1204-precise-64-[/FONT][FONT=arial]minimal ~ # teamviewer[/FONT]

[FONT=arial]root@Ubuntu-1204-precise-64-[/FONT][FONT=arial]minimal ~ # teamviewer[/FONT]

[FONT=arial]Init...[/FONT]
[FONT=arial]Checking setup...[/FONT]
[FONT=arial]Launching TeamViewer...[/FONT]
[FONT=arial]fixme:service:scmdatabase_[/FONT][FONT=arial]autostart_services Auto-start service L"MountMgr" failed to start: 2[/FONT]
[FONT=arial]fixme:service:scmdatabase_[/FONT][FONT=arial]autostart_services Auto-start service L"PlugPlay" failed to start: 2[/FONT]
[FONT=arial]fixme:actctx:parse_depend_[/FONT][FONT=arial]manifests Could not find dependent assembly L"Microsoft.Windows.Common-[/FONT][FONT=arial]Controls" (6.0.0.0)[/FONT]
[FONT=arial]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/[/FONT][FONT=arial]pkcs11/gnome-keyring-pkcs11.[/FONT][FONT=arial]so: /usr/lib/i386-linux-gnu/[/FONT][FONT=arial]pkcs11/gnome-keyring-pkcs11.[/FONT][FONT=arial]so: cannot open shared object file: No such file or directory[/FONT]
[FONT=arial]err:winediag:SECUR32_[/FONT][FONT=arial]initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.[/FONT]
[FONT=arial]fixme:heap:HeapSetInformation (nil) 1 (nil) 0[/FONT]
[FONT=arial]fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,([/FONT][FONT=arial]nil),0,(nil)) - stub![/FONT]
[FONT=arial]fixme:heap:HeapSetInformation (nil) 1 (nil) 0[/FONT]
[FONT=arial]fixme:process:[/FONT][FONT=arial]SetProcessShutdownParameters (00000100, 00000000): partial stub.[/FONT]
[FONT=arial]fixme:resource:GetGuiResources (0xffffffff,0): stub[/FONT]
[FONT=arial]fixme:win:EnumDisplayDevicesW ((null),0,0x32dc60,0x00000000)[/FONT][FONT=arial], stub![/FONT]
[FONT=arial]fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,[/FONT][FONT=arial]0x32d918,0x00000000), stub![/FONT]
[FONT=arial]fixme:win:EnumDisplayDevicesW ((null),1,0x32dc60,0x00000000)[/FONT][FONT=arial], stub![/FONT]
[FONT=arial]fixme:winhttp:[/FONT][FONT=arial]WinHttpDetectAutoProxyConfigUr[/FONT][FONT=arial]l discovery via DHCP not supported[/FONT]
[FONT=arial]fixme:msg:[/FONT][FONT=arial]ChangeWindowMessageFilter 233 00000001[/FONT]
[FONT=arial]fixme:msg:[/FONT][FONT=arial]ChangeWindowMessageFilter 4a 00000001[/FONT]
[FONT=arial]fixme:msg:[/FONT][FONT=arial]ChangeWindowMessageFilter 407 00000001[/FONT]
[FONT=arial]fixme:msg:[/FONT][FONT=arial]ChangeWindowMessageFilter 49 00000001[/FONT]
[FONT=arial]fixme:bitmap:[/FONT][FONT=arial]CreateBitmapIndirect planes = 0[/FONT]
[FONT=arial]fixme:bitmap:[/FONT][FONT=arial]CreateBitmapIndirect planes = 0[/FONT]
[FONT=arial]fixme:wtsapi:[/FONT][FONT=arial]WTSRegisterSessionNotification Stub 0x1005a 0x00000000[/FONT]
[FONT=arial]err: ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-[/FONT][FONT=arial]000000000046}[/FONT]
[FONT=arial]err: ole:marshal_object couldn't get IPSFactory buffer for interface {00000122-0000-0000-c000-[/FONT][FONT=arial]000000000046}[/FONT]
[FONT=arial]err: ole:StdMarshalImpl_[/FONT][FONT=arial]MarshalInterface Failed to create ifstub, hres=0x80040155[/FONT]
[FONT=arial]err: ole:CoMarshalInterface Failed to marshal the interface {00000122-0000-0000-c000-[/FONT][FONT=arial]000000000046}, 80040155[/FONT]
[FONT=arial]fixme:msg:[/FONT][FONT=arial]ChangeWindowMessageFilter c04f 00000001[/FONT]
[FONT=arial]fixme:winhttp:session_set_[/FONT][FONT=arial]option unimplemented option 101[/FONT]
[FONT=arial]fixme:winhttp:session_set_[/FONT][FONT=arial]option WINHTTP_OPTION_CONFIGURE_[/FONT][FONT=arial]PASSPORT_AUTH: 0x0[/FONT]
[FONT=arial]fixme:winhttp:session_set_[/FONT][FONT=arial]option unimplemented option 84[/FONT]
[FONT=arial]fixme:richedit:ME_[/FONT][FONT=arial]HandleMessage EM_SETFONTSIZE: stub[/FONT]
[FONT=arial]fixme:nls:GetGeoInfoW -1 4 0x32e1bc 3 0[/FONT]
[FONT=arial]err: ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-[/FONT][FONT=arial]c4579291692e} not registered[/FONT]
[FONT=arial]err: ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-[/FONT][FONT=arial]c4579291692e} could be created for context 0x1[/FONT]
[FONT=arial]err: ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-[/FONT][FONT=arial]c4579291692e} not registered[/FONT]
[FONT=arial]err: ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-[/FONT][FONT=arial]c4579291692e} could be created for context 0x1[/FONT]
[FONT=arial]fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0[/FONT]
[FONT=arial]fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0[/FONT]
[FONT=arial]fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0[/FONT]
[FONT=arial]fixme:nls:GetGeoInfoW -1 4 0x32dfc8 3 0[/FONT]
[FONT=arial]Terminated[/FONT][FONT=arial]

regards,[/FONT]

---

### Post by dave0109 on 2013-06-03
> /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

Are you running a 64-bit system?  If so, then that file is going to be in /usr/lib/x86_64-linux-gnu/pkcs11 instead and you'll need to check if Teamviewer supports 64-bit systems.  You may need to install some 32-bit compatibility libraries.

---

### Post by ahallubuntu on 2013-06-03
~

---

### Post by mirar2 on 2013-09-13
I have the exact same problem. 

It's weird - tracing it, it seems that something kills it after a few seconds. Note: ***terminated***.

```
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
read(7, 0x33dc68, 16)                   = ? ERESTARTSYS (To be restarted)
--- SIGTERM (Terminated) @ 0 (0) ---
+++ killed by SIGTERM +++
-------- user 1,596  kernel 2,480  elapsed 14,886

```
"killed by SIGTERM".

What goes around and kills teamviewers?

(As for libraries, it shows the first interface and lets you fill in stuff, then suddenly, TERMINATED.)

---

### Post by driftpost on 2013-10-02
You can try $sudo apt-get install libxtst6
lemme know if it helps. Cheers :idea:

---

