---
title: "Help with sh script"
date: 2013-09-20
forum: General Help
---

### Post by MrMusic25 on 2013-09-20
I have recently gotten into making simple scripts to make server management easier, but I cannot get this script to work. It's purpose is to move the current file to a backup, and then download the new version of the file. Can someone please check to make sure I am doing things correctly?

```
 
BUKKIT=http://dl.bukkit.org/downloads/craftbukkit/get/02342_1.6.2-R1.0/craftbukkit.jar


BENDING=/media/Data/Minecraft/Bending/minecraft-server.jar


CREATIVE=/media/Data/Minecraft/Creative/minecraft-server.jar


SURVIVAL=/media/Data/Minecraft/Survival/minecraft-server.jar


mv $BENDING ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $BENDING


mv $CREATIVE ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $CREATIVE


mv $SURVIVAL ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $SURVIVAL

```

I don't understand what I am doing wrong, I tried to make it so wget could simply override the old file, but from what I saw in the man page it isn't possible. Thanks for the help!

---

### Post by MG&amp;TL on 2013-09-20
> **MrMusic25 said:**
> 
```
 
BUKKIT=http://dl.bukkit.org/downloads/craftbukkit/get/02342_1.6.2-R1.0/craftbukkit.jar


BENDING=/media/Data/Minecraft/Bending/minecraft-server.jar


CREATIVE=/media/Data/Minecraft/Creative/minecraft-server.jar


SURVIVAL=/media/Data/Minecraft/Survival/minecraft-server.jar


mv $BENDING ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $BENDING


mv $CREATIVE ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $CREATIVE


mv $SURVIVAL ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT $SURVIVAL

```

I don't understand what I am doing wrong, I tried to make it so wget could simply override the old file, but from what I saw in the man page it isn't possible. Thanks for the help!

Sure you can, just use the -O option to write to a particular file.

For example:

```
wget ubuntu.com -O foo
cat foo
wget debian.org -O foo
cat foo
```

Using this in your script:

```

BUKKIT=http://dl.bukkit.org/downloads/craftbukkit/get/02342_1.6.2-R1.0/craftbukkit.jar


BENDING=/media/Data/Minecraft/Bending/minecraft-server.jar


CREATIVE=/media/Data/Minecraft/Creative/minecraft-server.jar


SURVIVAL=/media/Data/Minecraft/Survival/minecraft-server.jar


mv $BENDING ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT -O $BENDING


mv $CREATIVE ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT -O $CREATIVE


mv $SURVIVAL ./minecraft-server.jar.bak
wget -b --limit-rate=512k $BUKKIT -O $SURVIVAL
```

---

### Post by MrMusic25 on 2013-09-25
Thanks for the help, that worked! I also found I was accidentally using a dash instead of an underscore, which was probably the main issue... Thanks anyways!

---

