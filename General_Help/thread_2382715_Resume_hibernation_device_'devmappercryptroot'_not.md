---
title: "Resume hibernation device 'dev/mapper/cryptroot' not found"
date: 2018-01-16
forum: General Help
---

### Post by darkowic on 2018-01-16
[COLOR=#242729][FONT=Arial]I use Xubuntu 16.0.4 with encryption on the whole disk. I enabled hibernation.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]My PC was accidentally turn off because of no power. On boot - before even ask for encryption password I'm being dropped into emergency shell:

[/FONT][/COLOR]```
starting version 232
Error: resume hibernation device `/dev/mapper/cryptroot` not found
Error: device `/dev/mapper/cryptroot` not found. Skipping fsck
mount: you must specify the filesystem type
You are now being dropped into an emergency shell

```

[COLOR=#242729][FONT=Arial]I tried to decrypt my root partition and mount but I'm unable to mount the `cryptroot`[/FONT][/COLOR][COLOR=#242729][FONT=Arial]:

[/FONT][/COLOR]```
cryptroot luksOpen /dev/sdc3 cryptroot
mount /dev/mapper/cryptroot /new_root/
mount: unkown filesystem type `LVM2_member`

```

I'm lost. I have no idea what went wrong with the boot.

---

