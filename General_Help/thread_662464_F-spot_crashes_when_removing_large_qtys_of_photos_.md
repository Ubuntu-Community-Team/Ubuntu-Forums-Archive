---
title: "F-spot crashes when removing large qtys of photos from catalog"
date: 2008-01-09
forum: General Help
---

### Post by timzak on 2008-01-09
I have a large catalog of photos (8600+) that took very long to import into F-spot.  However, there were some glitches in the import process that prevented many photos from being imported.  When I re-imported my library, I ended up with two copies of my photos in the library, or 17000 entries.  Whenever I try to remove these entries from the F-spot catalog, F-spot greys out and I have to force quit.  I tried removing a few hundred at a time and that seems to work okay, but with 17000 entries, even a few hundred at a time will take a long time.  I tried removing around 2000 in one shot and that caused the grey-out lockup again.  

I want to remove the entire catalog and re-import it so I have one instance of each photo.  Is there a quick way to do this without causing F-spot to crash?

---

### Post by timzak on 2008-01-09
Update:

I've determined that you can manipulate up to 999 photos at a time without problem.  Once you go to 1000, F-spot crashes.  Is this a known limitation?

---

### Post by dillthedog on 2008-01-19
Dunno, but I've just encountered the same problem. I've posted on the f-spot mailing list. 

If you start f-spot from a terminal you'll see

[FONT="Courier New"]Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: 
Expression tree is too large (maximum depth 1000)
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr 
pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000]
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior 
behavior, Boolean want_results, System.Int32& rows_affected) [0x00000]
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000]
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]
Query: SELECT photos.id, photos.time, photos.uri, photos.description, 
photos.roll_id, photos.default_version_id FROM photos  WHERE  photos.id 
NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY 
photos.time
Syncing metadata to file...[/FONT]

and it sounds similar to what's reported in [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/134120](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/134120) 

Dougie

---

### Post by m.aicardi on 2008-01-21
Same problem here.

F-Spot hangs/crashes when removing 1000+ pictures. No problem  until 999 pictures, always hangs from 1000 on.

I think it could be an array-dimension related problem.

Cheers.

Marco

---

