---
title: "wine + MSN Messenger 7.0"
date: 2007-05-25
forum: General Help
---

### Post by ghell on 2007-05-25
I'm having trouble getting MSN Messenger 7.0 to work on wine. This is the first time I have used wine for anything (normally I just use the linux equivalents but in this case amsn does my head in and gaim/pidgin is great if you use multiple IMs but I only use MSN and it just lacks too many basic MSN specific features, so please do not just tell me to use an alternative. I want to use MSN Messenger.)

I followed the instructions at [http://wiki.winehq.org/MSN_Messenger_webcam_support](http://wiki.winehq.org/MSN_Messenger_webcam_support) but with the added native dll download and overrides shdocvw and shlwapi.

I get the following output:```
$ wine ~/.wine/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe
fixme:atl:AtlModuleInit SEMI-STUB (0x220121d0 0x22012254 0x22000000)
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 8 0x32fc10 0x32fc0c
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 16 0x32fc14 0x32fc10
fixme:wtsapi:WTSWaitSystemEvent Stub (nil) 0x00000018 0x7d3b09a4
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x17
fixme:ras:RasEnumConnectionsA (0x32f41c,0x32f410,0x32fb3c),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:iphlpapi:NotifyRouteChange (Handle 0x7c2589a4, overlapped 0x7c258984): stub
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:imm:ImmReleaseContext (0x10054, 0x155d88): stub
fixme:imm:ImmReleaseContext (0x10054, 0x155d88): stub
fixme:imm:ImmReleaseContext (0x10054, 0x155d88): stub
fixme:imm:ImmReleaseContext (0x10054, 0x155d88): stub
fixme:urlmon:URLMonikerImpl_BindToObject (0xd8cb70)->(0xd8cd88,(nil),{00000000-0000-0000-c000-000000000046},0x32ba64): stub
fixme:urlmon:URLMonikerImpl_BindToObject (0xd99100)->(0xd9ab48,(nil),{00000000-0000-0000-c000-000000000046},0x32e728): stub
fixme:urlmon:ObtainUserAgentString (0, 0xd9a8a0, 0x32f14c): stub
err:wininet:NETCON_init trying to use a SSL connection, but couldn't load libssl.so. Expect trouble.
fixme:nls:GetUserGeoID 16
```I mainly notice the SSL error that appears once and the winsock error that occurs every time it tries to log in.

I have read before that installing libssl will fix this, but I have openssl, libssl0.9.7 and libssl0.9.8 installed, and libssl is not in the repos.

---

### Post by d_xtremw on 2007-06-27
Has anyone found a solution for this yet cuz i wanna use msn messenger with wine as well

---

### Post by ghell on 2007-06-27
I got a little further on my Fedora box. It finds libssl on here and I can log in but I can't open conversation windows or see peoples names (I can tell who people are by holding over their names for the tooltip). About a minute later it crashes.

Still waiting for an answer on every single forum I have posted about this on.

---

### Post by s_h_a_d_o_w_s on 2007-06-27
[http://appdb.winehq.org/appview.php?iAppId=127](http://appdb.winehq.org/appview.php?iAppId=127)

---

### Post by tater_3001 on 2007-06-27
when microsoft made its agreements with novell i hoped the problem of no msn messanger for linux would be addressed but i guess not..

---

