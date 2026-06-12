---
title: "pmount: Permission problem with external hdd"
date: 2005-11-01
forum: General Help
---

### Post by blacksheep on 2005-11-01
Hi community!

I've an external usb harddisk with one big ext3 partition. Everytime I plug it in, it's mounted by pmount automatically under /media/[label_of_disk]. In general that's fine. But the mounted disk has a permission mask of 755!

As ordinary user I don't have write-permission but I want to use this hdd to store data and multimedia files on it.

Pmount is used for external hotplugging devices and I don't know where to change some settings to get write-permissions (e.g. a permission bitmask of 777).

Any ideas?

Thanks in advance, Michael.

---

### Post by felix_stegerman on 2005-11-01
If the disk is intended to be used by you as a normal user,
you should probable just make sure all the files belong to that user:
# sudo chown -R <username>: /media/<mountpoint>
This will recursively change the owner to <username>.


Felix

---

### Post by blacksheep on 2005-11-02
Thanks a lot Felix for the quick reply.

I tried it but it doesn't work for one exception: I can't create files / directories directly beneath /media/<mountpoint>. It still has the permission mask 755.

Any ideas about another solution?

best regards, Michael


[QUOTE=felix_stegerman]If the disk is intended to be used by you as a normal user,
you should probable just make sure all the files belong to that user:
# sudo chown -R <username>: /media/<mountpoint>
This will recursively change the owner to <username>.

Felix[/QUOTE]

---

### Post by felix_stegerman on 2005-11-02
Hi,

Could you tell me what the output of the 'mount' command is, after you
(or pmount) have mounted the disk ?

I'll try to see what happens if I format my usb thumbdrive as ext2 and whether
I get similar results ;-)


Felix

---

### Post by felix_stegerman on 2005-11-02
Formatting my usb key as ext2 and using chown (after mounting it) to change
the user worked for me. I'd still like to know what output mount gave you.


Felix

---

### Post by blacksheep on 2005-11-03
Hi Felix!

The output of mount is:
"/dev/sda1 on /media/PORTABLE type ext3 (rw,noexec,nosuid,nodev)".

But in the meantime i resolved the problem. After changing the owner with chown i, additionally, had to change the permissions with chmod to achieve write access to all folders. Now it's also possible to create folders directly beneath /media/<mountpoint>

Thanks a lot for your help!

Best regards Michael.

[QUOTE=felix_stegerman]Formatting my usb key as ext2 and using chown (after mounting it) to change
the user worked for me. I'd still like to know what output mount gave you.


Felix[/QUOTE]

---

