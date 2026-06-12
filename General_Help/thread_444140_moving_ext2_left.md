---
title: "moving ext2 left"
date: 2007-05-15
forum: General Help
---

### Post by mazy haze on 2007-05-15
hi folks,

**the question:**
how can i move etx2 partitions left?

**the story:**
i got some trouble editing my partitions.
the original situation was like that:

```

/dev/hda
  |- /dev/hda1: ntfs
  |- /dev/hda2: extended
  |    |- /dev/hda5: swap
  |    |- /dev/hda6: fat32
  |    |- /dev/hda7: ext3
  |- /dev/hda3: ext3

```

hda3 is my root partition, hda7 is where i store my stuff, hda1 and hda6 are used by windows.
hda7 was running out of space recently. since i haven't used my old windows during the last two or three years (got one running on virtualbox) i thought this would be a possible solution:

```

/dev/hda
  |- /dev/hda1: swap
  |- /dev/hda2: extended
  |    |- /dev/hda5: ext3
  |- /dev/hda3: ext3

```

i removed hda1, hda5 and hda6 using gparted just to find out gparted is not able to resize ext3. so i changed the file system to ext2:

```
tune2fs -O^has_journal /dev/hda5
```

(after deleting the other partitions hda5 was the new name of hda7)
now gparted was able to resize the partition, but only to the right.

so what i've got now is something like this:

```

/dev/hda
  |- /dev/hda1: swap
  |- some free space (4 gb)
  |- /dev/hda2: extended
  |    |- much free space (60 gb)
  |    |- /dev/hda5: ext2 (~ 80 gb files i would not like to lose)
  |- /dev/hda3: ext3

```

thanks a lot,
konstantin

---

### Post by ikonia on 2007-05-15
your in a bit of a jam on this one due to the position of your extended partition. 

I think (but I'm not certain) there is no way to move data around extended partitions.

---

### Post by mazy haze on 2007-05-16
solved. did it the hard way: moved data to a server, removed partitions, created new partitions, downloaded files... took a lot of time...
thanks anyway

---

