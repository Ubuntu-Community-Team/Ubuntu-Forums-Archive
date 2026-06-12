---
title: "Mount 2 partitions during boot"
date: 2007-04-26
forum: General Help
---

### Post by cari on 2007-04-26
Hi,

I have 2 partitions, one is mainly for OS, the other is for personal files.

My question is, what file should I edit, so that Ubuntu mounts them both by default and I don't have to mount my files partition manually after every boot-up.

Thanks in advance!

---

### Post by leg on 2007-04-26
/etc/fstab is the file you want. Look at what is there already and see if you can work it out. I would post mine but not on my machine at the moment.

---

### Post by hyperair on 2007-04-26
That'll be /etc/fstab.
Read how to edit it from the shell command "man fstab"

---

### Post by lw5 on 2007-04-26
There's a lot of mount info in the Ubuntu Wiki as well:

[link](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by cari on 2007-04-27
Thanks alot, I didn't get to the instructions given by link, however, I got everything working. Actually fstab already mounted my other partition into /dev/hda1:
```

# /dev/hda1 UUID=081849a8-eea3-4e08-81c3-dc2c108ed952 [COLOR="Red"]/dev/hda1 [/COLOR]      ext3    defaults        0       2

```

All I needed to do was to tell system to mount the device where I wanted and now everything works fine
```

# /dev/hda1 UUID=081849a8-eea3-4e08-81c3-dc2c108ed952 [COLOR="Red"]/home/markus/mnt [/COLOR]      ext3    defaults        0       2

```

I hope It'll help somone else too

Thanks :)

---

