---
title: "Starcraft launcher"
date: 2007-06-01
forum: General Help
---

### Post by thegrimgod on 2007-06-01
I'm trying to make a launcher that will both mount the SC cd and start starcraft in wine.
I have 2 launchers one that does 
sudo mount -t iso9660 -o loop /home/grim/.wine/drive_c/Program\ Files/Starcraft/iso/broodwar.iso /media/Starcraft
and the other 
wine /home/grim/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe
But when i have them both in one launcher using 
sudo mount -t iso9660 -o loop /home/grim/.wine/drive_c/Program\ Files/Starcraft/iso/broodwar.iso /media/Starcraft && wine /home/grim/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe
they both dont work. WHY?

---

### Post by ed_agamemnon on 2007-06-02
no idea, i'm affraid.

I launch my Starcraft like this:

```

#!bin/bash
cd "/home/me/.wine/drive_c/Program Files/Starcraft"
gksudo "mount -o loop sc.iso disk"
nice -n 20 wine starcraft.exe
cd "/home/me/.wine/drive_c/Program Files/Starcraft"
gksudo "umount disk"

```

that way, when i'm finished playing Starcraft, the .iso is automatically unmounted.

---

### Post by Lord Illidan on 2007-06-02
```

#!bin/bash
cd "/home/me/.wine/drive_c/Program Files/Starcraft"
gksudo "mount -o loop sc.iso disk"
nice -n 20 wine starcraft.exe
cd "/home/me/.wine/drive_c/Program Files/Starcraft"
gksudo "umount disk"
```

Why are you setting the priority of starcraft.exe to low? That way you are giving it the least favourable cpu priority.

---

### Post by Lord Illidan on 2007-06-02
Also, my cd is mounted automatically, when I insert it.

---

### Post by thegrimgod on 2007-06-02
Hm i might try a script as u suggest , Illidan , we are talking image cds here , they dont get mounted automatically and i read somewhere about the nice -n 20 stuff , or 0 dont kow which one is higher priority , but they didnt do anything for me, im also trying to find out how to get over the starcraft lag, so far no solution ,but i posted in the dapper howto starcraft thread, hope i get a solution, i tried some register stuff wiht no luck too

---

