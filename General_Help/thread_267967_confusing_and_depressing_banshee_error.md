---
title: "confusing and depressing banshee error"
date: 2006-09-29
forum: General Help
---

### Post by Sewage on 2006-09-29
Okay I guess backstory~ I had banshee installed but it wasn't running well on this computer, I decided to use an older version (the one in the dapper packages) hoping that it would work better~ I removed the current build but it had an error of some sort, after trying somethings it seemed to uninstall, I went on to comment out the bit in my sources list that I got from banshee's website that kept me on the newest version, and reinstalled banshee using the version that comes with dapper.

now it doesn't work at all, it looks like it installed alright~ but nothing happened when I click the icon! when i type it in terminal this is what I get (see below) i am pretty lost. D:

banshee

** (/usr/lib/banshee/banshee.exe:7621): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=14)
     Version:    1.0.5000.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:7621): WARNING **: Could not load file or assembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies. : Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
  at <0x00000> <unknown method>
  at Banshee.Base.Globals.Initialize () [0x00000]
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000]
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000]

---

