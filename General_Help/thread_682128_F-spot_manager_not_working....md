---
title: "F-spot manager not working..."
date: 2008-01-29
forum: General Help
---

### Post by Fireblend on 2008-01-29
So, I tried to use F-Spot earlier but it doesn;t seem to work. Here's the terminal output:

```
~$ f-spot
Initializing Mono.Addins
Starting new FSpot server
/home/sergio/.gtkrc-2.0:35: error: scanner: unterminated string constant - e.g. `style'

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

```

Any idea what could be causing this? I've never used it before, but it comes with Ubuntu and should work well, right? Any help would be greatly appreciated.

---

### Post by Fireblend on 2008-01-29
Still not working. Anyone?

---

### Post by Valehru on 2008-04-13
Have the same problem.

pawn ~: f-spot
Initializing Mono.Addins
Starting new FSpot server

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

---

### Post by gerryk on 2008-04-25
This seems to be related to running the hardy version of f-spot using previous configuration files.

try

$ rm -rf ~/.gnome2/f-spot

and restart f-spot

---

### Post by devil404 on 2008-06-15
Cool! Works for me now! I was having the same problem as the above users.

---

