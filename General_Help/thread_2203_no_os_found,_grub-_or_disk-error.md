---
title: "no os found, grub- or disk-error"
date: 2004-10-26
forum: General Help
---

### Post by silverkhan on 2004-10-26
I've installed ubuntu on a machine with win2k on another physical disk... the disk withe ubuntupartitions on also has a 36gb ntfs partition with different stuff (music, pictures and so on).
I tried to mount the 36gb ntfs filesystem, but when i rebooted the computer somthing strange happend. When grub is supposed to be loaded, the machine says "no operation system found"...

After discussing this matter with people on the net, I've reached the conlusion that either has one of the disks crashed or something has happended with grub.

I don't think that this actually has anything to do with me installing ubuntu, but since this is the first time I've used grub, i wonder: where does the ubuntu installation installs grub? 

I've been told that different distros handles the grub installation/configuration differently, so how is this done i ubuntu?

i hope this has'nt been answered before  :)

---

### Post by Kopf on 2004-10-26
It usually installs it on the MBR of hda.  DO you have a boot disk?

Kopf

---

### Post by silverkhan on 2004-10-26
[QUOTE=Kopf]It usually installs it on the MBR of hda.  DO you have a boot disk?

Kopf[/QUOTE]
 boot disk? you mean like a floppy or a cd? I have tried RIP, but i did not manage to mount any of the disks

i think the hda disk has crashed and most likely grub with it... If I'll set the current slave disk as master, how can i install grub, and make bios recognize it?

---

### Post by silverkhan on 2004-10-26
ok, now don't ask me why, but when I turned on the computer five minutes ago, i noticed that when the bios was doin' its thing it listed two things which i hadn't seen yesterday evening:

Fixed disk: <disk manufacturer of hda>
Fixed disk: <disk manufacturer of hdb>

and my little cute ubuntu booted perfectly [-o< 
I have yet to try win2k, but i don't se why it should not work. It showed up in grub, but if it doesn't work, then why bother with it :) 

It must be disk gnomes... definetly disk gnomes...

---

