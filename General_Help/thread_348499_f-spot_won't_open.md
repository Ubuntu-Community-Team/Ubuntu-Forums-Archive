---
title: "f-spot won't open"
date: 2007-01-28
forum: General Help
---

### Post by TheRingmaster on 2007-01-28
I can't seem to get my f-spot application to open. I am on ubuntu edgy if this helps. When I open it in a terminal I get this-->> :~$ f-spot
Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr pzTail, System.IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32 rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at TagStore.LoadAllTags () [0x00000] 
  at TagStore..ctor (Mono.Data.SqliteClient.SqliteConnection connection, Boolean is_new) [0x00000] 
  at Db.Init (System.String path, Boolean create_if_missing) [0x00000] 
  at FSpot.Core..ctor () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
XXXXX
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
        [0xb736ac11]
        [0xb736ab9c]
        [0xb4f3669c]
        [0xb4f3666e]
        [0xb4f365e9]
        mono [0x80af103]
        mono [0x81158f1]
        mono [0x80af237]
        mono [0x80c6444]
        mono [0x810984e]
        mono [0x811fbf5]
        /lib/tls/i686/cmov/libpthread.so.0 [0xb7e58504]
        /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7dc651e]
Aborted (core dumped)


---

### Post by TheRingmaster on 2007-01-29
bump

---

### Post by TheRingmaster on 2007-01-29
bump again

---

### Post by TheRingmaster on 2007-01-29
Bump (anyone out there???)

---

### Post by TheRingmaster on 2007-01-30
bump---anyone at all!!:confused:

---

### Post by TheRingmaster on 2007-01-31
bump once more

---

### Post by TheRingmaster on 2007-02-02
:( bump (Some moderator is going to have to deletes some of my bump pretty soon.)

---

### Post by risbac on 2007-02-03
Looks like a db problem from your error message. 

Was it a fresh install of F-spot, or did you upgrade from a previous version of Ubuntu?

---

### Post by TheRingmaster on 2007-02-03
> **risbac said:**
> Looks like a db problem from your error message. 

Was it a fresh install of F-spot, or did you upgrade from a previous version of Ubuntu?


This is a fresh install of ubuntu edgy. I never noticed this problem until now.

---

### Post by colgate on 2007-02-05
i get the same problem.
fresh install, too.

---

### Post by TheRingmaster on 2007-02-07
anyone??????

I found this over at the gnewsense bug reporter. 
[gNewSense Bugs | Bugs / F-spot won't start]("http://bugs.gnewsense.org/Bugs/00033")

When I do it, it asks me to downgrade some mono things. I am a little scared to do it.

---

### Post by Tomosaur on 2007-02-09
> **TheRingmaster said:**
> I can't seem to get my f-spot application to open. I am on ubuntu edgy if this helps. When I open it in a terminal I get this-->

It does certainly seem like a Mono error. Have you tried reinstalling Mono and F-Spot? If not, try that first.
```

sudo aptitude reinstall mono f-spot

```
Good luck :)

---

### Post by lamego on 2007-02-09
What version are you running ?

I am running the latest version on Edgy without problems:
[http://www.getdeb.net/app.php?name=f-spot](http://www.getdeb.net/app.php?name=f-spot)

---

### Post by TheRingmaster on 2007-02-09
> **Tomosaur said:**
> It does certainly seem like a Mono error. Have you tried reinstalling Mono and F-Spot? If not, try that first.
```

sudo aptitude reinstall mono f-spot

```Good luck :)


ok I did that 

I still get a similar message though
> desktop:~$ f-spot
Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr pzTail, System.IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32 rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at TagStore.LoadAllTags () [0x00000] 
  at TagStore..ctor (Mono.Data.SqliteClient.SqliteConnection connection, Boolean is_new) [0x00000] 
  at Db.Init (System.String path, Boolean create_if_missing) [0x00000] 
  at FSpot.Core..ctor () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
XXXXX
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
        [0xb7362c11]
        [0xb7362b9c]
        [0xb4f2e69c]
        [0xb4f2e66e]
        [0xb4f2e5e9]
        mono [0x80af103]
        mono [0x81158f1]
        mono [0x80af237]
        mono [0x80c6444]
        mono [0x810984e]
        mono [0x811fbf5]
        /lib/tls/i686/cmov/libpthread.so.0 [0xb7e50504]
        /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7dbe51e]
Aborted (core dumped)


---

### Post by TheRingmaster on 2007-02-09
> **lamego said:**
> What version are you running ?

I am running the latest version on Edgy without problems:
[http://www.getdeb.net/app.php?name=f-spot](http://www.getdeb.net/app.php?name=f-spot)


f-spot version is 0.2.1-1ubuntu1

There are many packages with mono in there name. You have to me more specific.

---

### Post by TheRingmaster on 2007-02-12
hello??? where did all of you go to?

---

### Post by dm1024 on 2007-02-12
I have such mesages. I've delete this file
$HOME/.gnome2/f-spot/photos.db
and it starts and works. Try this.

This originally was taken from 
[http://sbug.no-ip.info/words/2006-03-26-45](http://sbug.no-ip.info/words/2006-03-26-45)
but I modified it ;-)

---

### Post by TheRingmaster on 2007-02-12
> **dm1024 said:**
> I have such mesages. I've delete this file
$HOME/.gnome2/f-spot/photos.db
and it starts and works. Try this.

This originally was taken from 
[http://sbug.no-ip.info/words/2006-03-26-45](http://sbug.no-ip.info/words/2006-03-26-45)
but I modified it ;-)
thanks that worked!

---

### Post by jeffrash on 2008-06-20
Thanks, That worked for me too.

---

