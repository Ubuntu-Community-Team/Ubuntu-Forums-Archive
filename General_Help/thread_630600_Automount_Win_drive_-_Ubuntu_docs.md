---
title: "Automount Win drive - Ubuntu docs"
date: 2007-12-03
forum: General Help
---

### Post by NJC on 2007-12-03
While search for Automounting fat32 Win drives in the Ubuntu documentation, I see 2 methods: 
 
```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```
[https://help.ubuntu.com/community/MountingWindowsPartitions#head-58b0f4b165129f43a80bba6c1c4227c490efa119](https://help.ubuntu.com/community/MountingWindowsPartitions#head-58b0f4b165129f43a80bba6c1c4227c490efa119)
 
And the following. First, a mount accesible by everyone:
 
```

user,auto,fmask=0111,dmask=0000

```
 
Second, Accessible by a subset of users:```

user,auto,fmask=0177,dmask=0077,uid=1000

```[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6)
 
In both Ubuntu 6.06 and 7.10 I've seen errors regarding using "iocharset=utf8" for automounting drives. So which is it, first or second method? I continue to have Permissions grief using Method #1 so I'm going back to Method #2 - but can this information be consolidated into one page as it's conflicting and confusing.

---

### Post by metalheart on 2007-12-03
You are referring to community documentation, 'how-to do things'. man mount, man fstab is 'how thing are'.

---

