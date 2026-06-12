---
title: "Problems importing pictures with f-spot"
date: 2007-07-09
forum: General Help
---

### Post by tgcUbuntu on 2007-07-09
I am trying to import all my pictures using f-spot. I run f-spot. I choose File->Import and then select my pictures partition /media/pictures. It starts importing them but only gets to file #288 of 2800 pictures and then gives the error:
     Error opening /media/pictures/2004/20040415/CRW0388.CRW
     Too many open files
And then it gives the option to Skip or Cancel. If I select Skip, it just gives the same message with another file.

Any idea what the problem is here?

---

### Post by rax_m on 2007-07-11
Sorry.. haven't seen this issue.
Are you copying the photo to the f-spot location as well or just adding existing photos to the albums?
Also, am I right in assuming these are raw images? so quite large?

You could try importing a subdirectory at a time.. a pain but it might work. 

Sorry if I wasn't much help :-/

---

### Post by tgcUbuntu on 2007-07-11
I am trying to import existing photo's.  I have a special partition set up to hold all my photos. So when I run f-spot and do the Import I set it so that it doesn't copy the photo's, just include them in the catalog.

I ran f-spot from a terminal and these are the errors that I got:

open uri = file:///media/pictures/2004/2004_05_16/CRW_0478.CRW
reading 0 5218404
reading 1 5218414
reading 2 5218424
reading 3 5218434
reading 0 5218268
reading 1 5218278
reading 2 5218288
reading 3 5218298
reading 4 5218308
reading 5 5218318
reading 6 5218328
reading 7 5218338
reading 8 5218348
reading 9 5218358
reading 10 5218368
reading 11 5218378
reading 12 5218388
reading 0 5210280
reading 1 5210290
reading 2 5210300
0x101
open uri = file:///media/pictures/2004/2004_05_16/CRW_0479.CRW
reading 0 5188838
reading 1 5188848
reading 2 5188858
reading 3 5188868
reading 0 5188702
reading 1 5188712
reading 2 5188722
reading 3 5188732
reading 4 5188742
reading 5 5188752
reading 6 5188762
reading 7 5188772
reading 8 5188782
reading 9 5188792
reading 10 5188802
reading 11 5188812
reading 12 5188822
Error importing /media/pictures/2004/2004_05_16/CRW_0479.CRW
Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteStatement (intptr,int&,intptr&,intptr&)
  at Mono.Data.SqliteClient.SqliteDataReader.ReadpVm (IntPtr pVm, Int32 version, Mono.Data.SqliteClient.SqliteCommand cmd) [0x00000] 
  at Mono.Data.SqliteClient.SqliteDataReader..ctor (Mono.Data.SqliteClient.SqliteCommand cmd, IntPtr pVm, Int32 version) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteDataReader:.ctor (Mono.Data.SqliteClient.SqliteCommand,intptr,int)
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteScalar () [0x00000] 
  at PhotoStore.Create (System.String newPath, System.String origPath, Gdk.Pixbuf& thumbnail) [0x00000] 
  at PhotoStore.Create (System.String path, Gdk.Pixbuf& thumbnail) [0x00000] 
  at FileImportBackend.Step (.Photo& photo, Gdk.Pixbuf& thumbnail, System.Int32& count) [0x00000] 

(f-spot:7069): Gtk-WARNING **: Error loading icon: Failed to open file '/home/ted/.themes/tish/gtk-2.0/icons/gtk-dialog-error.png': Too many open files

I checked out the file that it was trying to import(CRW_0479.CRW and it seems ok.  It says something about an SQL error or missing database and I don't have any idea what that's about. Also at the end of the listing is another error about loading an icon. I checked out the file and it also seems ok.

---

### Post by rax_m on 2007-07-12
I do EXACTLY what you do for my pictures. I have all my pics on a FAT32 partition and import into f-spot without copying. I have imported approximately 3500+ pictures (some raw most jpg) without any issues. 

I know that f-spot uses a sqllite database for storing tag information. I think it stores this in ~/.gnome2/f-spot directory. Could this file maybe be corrupted or something?? 

You could report this as a bug. The only other thing I would've tried is deleting the photos.db file created in the above directory and trying to import from scratch. But don't blame me if it breaks stuff worse ;)

---

