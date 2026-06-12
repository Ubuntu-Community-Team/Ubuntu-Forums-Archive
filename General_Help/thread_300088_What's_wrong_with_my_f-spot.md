---
title: "What's wrong with my f-spot"
date: 2006-11-15
forum: General Help
---

### Post by philyer on 2006-11-15
I'm using edgy.
F-spot cannot be started, but it was fine yesterday.
I have restarted the computer, but it's not helpful.
I've started f-spot in the termal, codes are below:
```
$ f-spot
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

Starting new FSpot server
Starting new FSpot server
        mono(mono_handle_native_sigsegv+0xde) [0x815644e]
        mono [0x8122c88]
        [0xffffe440]
        mono [0x80c3ab3]
        [0xb7915c11]
        [0xb7915b9c]
        [0xb600b4c4]
        [0xb600b496]
        [0xb600b411]
        mono [0x80af103]
        mono [0x81158f1]
        mono [0x80af237]
        mono [0x80c6444]
        mono [0x810984e]
        mono [0x811fbf5]
        /lib/tls/i686/cmov/libpthread.so.0 [0xb7ead504]
        /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7e1b51e]
Aborted (core dumped)

```
What's wrong with it? How can I repair it?

---

### Post by kxs on 2006-12-11
I get the same error :(

---

### Post by jsievert on 2006-12-11
Found this fix for the same problem, worked for me.

[https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910/comments/2]("https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910/comments/2")

---

### Post by kxs on 2006-12-12
as mentioned in the link you posted I should do this:
```
cp $HOME/.gnome2/f-spot/photos.db $HOME/.gnome2/f-spot/photos.db-BACKUP
sqlite $HOME/.gnome2/f-spot/photos.db .dump | sqlite3 out.db
mv out.db $HOME/.gnome2/f-spot/photos.db
```
but after:
```
sqlite $HOME/.gnome2/f-spot/photos.db .dump | sqlite3 out.db
```
I get:
```
Unable to open database "/home/krzysiek/.gnome2/f-spot/photos.db": file is encrypted or is not a database
```
and I don`t know what to do with this :(

---

### Post by ckoester on 2007-08-06
I had the same problem.  Try replacing sqlite with sqlite3 at the beginning:

```
sqlite3 $HOME/.gnome2/f-spot/photos.db .dump | sqlite3 out.db
```

---

