---
title: "Cannot unrar all files in archive"
date: 2013-06-30
forum: General Help
---

### Post by Charkel on 2013-06-30
I bought a VPS and is currently to install a minecraft server. I compressed my current server on my computer to  a RAR and sent it to the server.
But now when I try to extract I get Fail on half the files :(

```
root@charkel:/home# mkdir bukkit
root@charkel:/home# sudo unrar -xf BukkitServer.rar bukkit

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/BukkitServer.rar

Extracting  plugins/ClearLag/config.yml                               Failed
Extracting  plugins/ClearLag/customClears.yml                         Failed
Extracting  plugins/Clearlag.jar                                      Failed
Extracting  plugins/Fly.jar                                           Failed
Extracting  plugins/Multiverse-Core/config.yml                        Failed
Extracting  plugins/Multiverse-Core/debug.log                         Failed
Extracting  plugins/Multiverse-Core/debug.log.lck                     OK
Extracting  plugins/Multiverse-Core/worlds.yml                        Failed
Extracting  plugins/Multiverse-Core-2.4.jar                           Failed
Extracting  plugins/SetSpawn.jar                                      Failed
Extracting  plugins/Simple-AutoSave/config.yml                        Failed
Extracting  plugins/Simple-AutoSave.jar                               Failed
Extracting  plugins/WorldEdit/config.yml                              Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_145.class         Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_146.class         Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_147.class         Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_15.class          Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_152.class         Failed
Extracting  plugins/WorldEdit/nmsblocks/CBXNmsBlock_prePackage.class  Failed
Extracting  plugins/WorldEdit/nmsblocks/MCPCPlusXNmsBlock_147.class   Failed
Extracting  plugins/WorldEdit/nmsblocks/MCPCPlusXNmsBlock_151dv.class Failed
Extracting  plugins/WorldEdit/worldedit.log                           OK
Extracting  plugins/WorldEdit/worldedit.log.lck                       OK
Extracting  plugins/WorldEdit.jar                                     Failed
Extracting  Suupaflat/data/villages.dat                               OK
Extracting  Suupaflat/level.dat                                       OK
Extracting  Suupaflat/level.dat_mcr                                   OK
Extracting  Suupaflat/level.dat_old                                   OK
Extracting  Suupaflat/players/Charkel.dat                             OK
Extracting  Suupaflat/players/kallsup.dat                             OK
Extracting  Suupaflat/players/Ldde.dat                               OK
Extracting  Suupaflat/players/sherl0x.dat                             OK
Extracting  Suupaflat/region/r.-1.-1.mca                              Failed
Extracting  Suupaflat/region/r.-1.0.mca                               Failed
Extracting  Suupaflat/region/r.-1.1.mca                               Failed
Extracting  Suupaflat/region/r.-1.2.mca                               Failed
Extracting  Suupaflat/region/r.-2.0.mca                               Failed
Extracting  Suupaflat/region/r.-2.1.mca                               Failed
Extracting  Suupaflat/region/r.0.-1.mca                               Failed
Extracting  Suupaflat/region/r.0.0.mca                                Failed
Extracting  Suupaflat/region/r.0.1.mca                                Failed
Extracting  Suupaflat/region/r.1.0.mca                                Failed
Extracting  Suupaflat/session.lock                                    OK
Extracting  Suupaflat/uid.dat                                         OK
Extracting  ops.txt                                                   OK
Extracting  server.properties                                         Failed
32 Failed
root@charkel:/home#

```

Why is this? :(

---

### Post by MidnightGrey on 2013-06-30
check the md5sum of the rar file from your server and your desktop to see if they match.
you can get the md5sum by using this command:
```
 md5sum <filename> 
```

if the values dont match then i guess the copy didnt send correctly.

---

