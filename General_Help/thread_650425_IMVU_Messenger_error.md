---
title: "IMVU Messenger error"
date: 2007-12-26
forum: General Help
---

### Post by ULAMSS5 on 2007-12-26
when i use imvu, wine appears and stuff, it goes well pretty well, execpt its laggy, really laggy. anyways thats not the problem. the problem is, the "tutorial" window which appears inside the wine window, it stays black, when i move my cursor around it'll turn into a hand at some points, (i assume those are places i can click). but the window is always black. what should i do?

---

### Post by TidusBlade on 2007-12-26
You can check on the WINE AppDB for comment on what to do, [here](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3927) although they are talking about the Beta...

---

### Post by ULAMSS5 on 2007-12-27
don't see how can that do me good, anyways. i noticed that it can "work" but still, the messenger windows is black but to the left, you'll see the things. and if you try to click on that, you'll just end up clicking at the desktop. so i had to figure around things with a black window, according to where the buttons are, i move my cursor aproximately to that place in the black window. really inconvenient. how do i fix it?

---

### Post by DenKain on 2008-02-24
Well my installation will start and then crash. Here is the output from the command line.

```

denkain@saber:~$ wine "/home/denkain/.wine/drive_c/Program Files/IMVU/IMVUClient.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
err:ole:create_server class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} could be created for context 0x15
fixme:secur32:schan_FreeCredentialsHandle (0x25acde8): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x235f3a0)->(0x9ac,0x34d7c0): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x235f3a0)->(0x9ac,0x34d608): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34bb37, 0x34bb38): stub
fixme:urlmon:ObtainUserAgentString (0, 0x25acfe8, 0x34bb38): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x235f3a0)->(0x9ac,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x235f3a0)->(0x9ac,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x235f3a0)->(0x9ac,0x34d774): Stub!
fixme:wininet:InternetLockRequestFile STUB
DRM_I830_CMDBUFFER: -22
denkain@saber:~$ wine "/home/denkain/.wine/drive_c/Program Files/IMVU/IMVUClient.exe" -dx8
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
denkain@saber:~$ wine "/home/denkain/.wine/drive_c/Program Files/IMVU/IMVUClient.exe" -dx8
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
err:ole:create_server class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} could be created for context 0x15
fixme:secur32:schan_FreeCredentialsHandle (0x246fcb8): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x269fa78)->(0xb4c,0x34d7c0): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x269fa78)->(0xb4c,0x34d608): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34bb37, 0x34bb38): stub
fixme:urlmon:ObtainUserAgentString (0, 0x28a9d60, 0x34bb38): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x269fa78)->(0xb4c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x269fa78)->(0xb4c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x269fa78)->(0xb4c,0x34d774): Stub!
fixme:wininet:InternetLockRequestFile STUB
DRM_I830_CMDBUFFER: -22
denkain@saber:~$ wine "/home/denkain/.wine/drive_c/Program Files/IMVU/IMVUClient.exe" -gpl
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
err:ole:create_server class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} could be created for context 0x15
fixme:secur32:schan_FreeCredentialsHandle (0x26bef20): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470578)->(0x96c,0x34d7c0): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470578)->(0x96c,0x34d608): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34bb37, 0x34bb38): stub
fixme:urlmon:ObtainUserAgentString (0, 0x26bf978, 0x34bb38): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470578)->(0x96c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470578)->(0x96c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470578)->(0x96c,0x34d774): Stub!
DRM_I830_CMDBUFFER: -22
denkain@saber:~$ err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
err:ole:create_server class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} could be created for context 0x15
fixme:secur32:schan_FreeCredentialsHandle (0x249da78): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x26a0350)->(0x96c,0x34d7c0): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x26a0350)->(0x96c,0x34d608): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34bb37, 0x34bb38): stub
fixme:urlmon:ObtainUserAgentString (0, 0x249dc78, 0x34bb38): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x26a0350)->(0x96c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x26a0350)->(0x96c,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x26a0350)->(0x96c,0x34d774): Stub!
DRM_I830_CMDBUFFER: -22

denkain@saber:~$ clear

denkain@saber:~$ wine "/home/denkain/.wine/drive_c/Program Files/IMVU/IMVUClient.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34dd4c,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
err:ole:create_server class {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bb8b07a0-b8d1-44e0-a262-c9b7212aec68} could be created for context 0x15
fixme:secur32:schan_FreeCredentialsHandle (0x21aa08): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470f40)->(0x9c0,0x34d7c0): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470f40)->(0x9c0,0x34d608): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34bb37, 0x34bb38): stub
fixme:urlmon:ObtainUserAgentString (0, 0x28da678, 0x34bb38): stub
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470f40)->(0x9c0,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470f40)->(0x9c0,0x34d774): Stub!
fixme:ddraw:IDirectDrawImpl_GetSurfaceFromDC (0x2470f40)->(0x9c0,0x34d774): Stub!
fixme:wininet:InternetLockRequestFile STUB
DRM_I830_CMDBUFFER: -22


```

---

### Post by DenKain on 2008-03-15
bump

---

### Post by SneakyWho_am_i on 2008-04-08
problem: black 3d window
suggested solution: imvu inventory window, hit "settings", then change the rending mode to standard. experiement, one of the three will work (+/-)

In the latest version of Xubuntu Hardy with Wine (not looking up the version numbers, sorry) it works.........

sorta....

What works:
- loading products like clothes
- chatting
- everything outside the 3d window

what doesn't work (compare this to the stuff at winedb)
- loading imvu urls (although there is a workaround for this at the wine application database)
- entering public rooms (for me anyway it just remains in the already loaded room)
- text chat (more on this in a second)
- direct3d and opengl (for me, they don't work. for others they work, ymmv)

how i set it up:

- install imvu
- upgrade to the latest version (you, like me, are probably surprised to find the application can download a newer binary that what you can reach from your web browser...)
- turn OFF text chat as it doesn't work for some reason in WINE, and if it's on you will be unable to type anything
- close the 3d window. turn off the turorial, turn off "load 3d window when app starts", turn off 'start imvu wwith windows"
- open the 3d window
- IF the 3d window is black, change the rending mode to opengl and close the 3d window, then open it again
- IF the 3d window is black, change the rendering mode to standard and close the 3d window, then open it again
- IF it's too slow, try lowernig the target framerate, closing the 3d window, and opening it again (they do try to make this as painful as possible, huh?)

Things that might help (but probably won't - these are all in wine config):
- turning off vector shading
- turning off pixmapping
- change compatability mode to wnidows 98
- turn off window manager window managemtnt (huh?)
- turn on virtual desktop

Those things that MIGHT help did nothing for me, but others have recommended themto me so they're worth inclusion I think.

Afterwards I noted these things:
- can't enter public rooms (no great loss)
- can't load imvu: urls in firefox for obvious reasons
- the colours were....... stuffed. i look like i'm made of pink skittles. the text in the speech bubbles is unreadable.
- every part of the interface works!! Everything!! Except you have to use left mouse button to scroll in the iventory window, no scroll wheel - but who cares? :D
- It's FAST, way faster than it was in Windows

So PROBLEM:
- can't read speech bubbles
WORKAROUND:
- resize the window and learn to read really fast. You'll see what I mean when you try it.
SOLUTION:
- still looking. Need a windows dll???

NOTES ON OTHER VERSIONS
An earlier version of wine reproduced the graphics very faithfully.
0.9.94 maybe??
Problem was it was unbearably slow, practically unusable. However, D3d and OpenGL worked in that version *I think*

Very early versions of wine have no networking and will be useless, so don't try going back in time too far

I couldn't get imvu's previewer to work, but I didn't try very hard.

[b]Second Life has a downloadable package or binary for their client (which i think was now open source) and it is probably worth checking that out. It will probably run a lot more smoothly than imvu and is worth a look in, particularly if you want to speak to adults
all in my humble opinion.[/b]
I hope this helps you a little bit at least, anyway.
Let us know how it turns out in the end!

---

### Post by SneakyWho_am_i on 2008-04-08
DenKain, your console output was very helpful, quick fix for your installatio woes should be:

```
sudo apt-get install winbind
```

---

