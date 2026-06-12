---
title: "F-Spot failing to load"
date: 2007-11-21
forum: General Help
---

### Post by FleetAdmiral74 on 2007-11-21
Heres what I get in terminal, 

```
fed@ed-desktop:~$ f-spot
Initializing Mono.Addins
Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
Updated database from version 2 to 3

```

It then just stays like that. I did this after a complete removal / install. 

I have Gutsy.

---

