---
title: "Need help re-installng F-Spot"
date: 2007-03-10
forum: General Help
---

### Post by Roger Mudd on 2007-03-10
Need a little help. I made an effort to install the most recent versions of F-Spot and Banshee recently. I failed miserably and now F-Spot will not start up.
Here's the output from the terminal when I attempt to run F-Spot.

```
Starting new FSpot server
XXXXX
System.Exception: Unsupported database version
  at Db.Init (System.String path, Boolean create_if_missing) [0x00000] 
  at FSpot.Core..ctor () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
XXXXX
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server
Starting new FSpot server

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:

  at (wrapper managed-to-native) System.Threading.Monitor.Monitor_try_enter (object,int) <0x00004>
  at (wrapper managed-to-native) System.Threading.Monitor.Monitor_try_enter (object,int) <0xffffffff>
  at System.Threading.Monitor.Enter (object) <0x00013>
  at (wrapper synchronized) DBus.Service.remove_SignalCalled (DBus.Service/SignalCalledHandler) <0xffffffff>
  at FSpot.Core.Proxy.Finalize () <0x00015>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        mono(mono_handle_native_sigsegv+0xde) [0x815644e]
        mono [0x8122c88]
        [0xffffe440]
        mono [0x80c3ab3]
        [0xb73a3c11]
        [0xb73a3b9c]
        [0xb5ee066c]
        [0xb5ee063e]
        [0xb5ee05b9]
        mono [0x80af103]
        mono [0x81158f1]
        mono [0x80af237]
        mono [0x80c6444]
        mono [0x810984e]
        mono [0x811fbf5]
        /lib/tls/i686/cmov/libpthread.so.0 [0xb7e91504]
        /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7dff51e]
Aborted (core dumped)
```

I've tried reinstalling from Synaptic and the command line as well as dpkg-reconfigure. Nothing has worked. I'm assuming this is a Mono issue as both F-Spot and Banshee utilize Mono. However, Tomboy (another Mono application) runs perfectly fine.
Any input is greatly appreciated.

Roger

---

