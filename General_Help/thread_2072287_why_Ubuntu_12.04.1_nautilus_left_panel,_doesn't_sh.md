---
title: "why Ubuntu 12.04.1 nautilus left panel, doesn't show other partitions and usb drives?"
date: 2012-10-17
forum: General Help
---

### Post by amerllica on 2012-10-17
how do you do friends
will be fine
I had Ubuntu 12.04 and all thing work well but at one day i decide to change my partition tables, and done it.
at now I've windows 8, Ubuntu 12.04.1 and Backtrack5 R3 on my laptop.
my partitions are:
```

/dev/sda1   *        2048    58597375    29297664    7  HPFS/NTFS/exFAT
/dev/sda2        58601472   976773119   459085824    5  Extended
/dev/sda5        58605120   797020159   369207520    7  HPFS/NTFS/exFAT
/dev/sda6       797030400   933763071    68366336   83  Linux
/dev/sda7       933765120   972834815    19534848   83  Linux
/dev/sda8       972836864   976773119     1968128   82  Linux swap / Solaris

```at first I install windows 8 and then Backtrack5 R3, and at last I install Ubuntu 12.04.1 and I realize that my Ubuntu nautilus doesn't show other partitions or usb/cd/dvd drives. I search in Google and various Linux or Ubuntu forums, But I can't find any solution, just one thing... that is "[FONT=tahoma,sans-serif]gvfs-gdu-volume[/FONT]" cause nautilus left panel show other partitions which didn't mounted. but when I see```
top
```there isn't this program.
who can I solve this problem? how nautilus can show other partitions or drives in its left panel once again?

---

### Post by dcstar on 2012-10-18
> **amerllica said:**
> 
.........
who can I solve this problem? how nautilus can show other partitions or drives in its left panel once again?

Take them out of /etc/fstab.

Permanently mounted partitions are not displayed in Nautilus because **you** already have them mounted in places **you** obviously want them.

---

### Post by mcduck on 2012-10-18
> **dcstar said:**
> Take them out of /etc/fstab.

Permanently mounted partitions are not displayed in Nautilus because **you** already have them mounted in places **you** obviously want them.

...unless they are mounted into a directory inside /media, using fstab or not :)

---

### Post by shreepads on 2012-10-18
> **mcduck said:**
> ...unless they are mounted into a directory inside /media, using fstab or not :)

Or you drag and drop them into the left panel inside Nautilus...

---

### Post by amerllica on 2012-10-18
no no no friends
i mean in my nautilus left pane there were three categories,

[LIST=1]
[*]Devices
[*]Computer
[*]Network
[/LIST]
but when i install ubuntu 12.04.1 my nautilus doesn't show Devices categories.
already, nautilus show devices in default mode, the devices that had not mounted.
like my other partitions. and when i had plug in my usb cool disk, nautilus show it in left panel in devices category and mount it automaticly. but at now i must mount all off other partitions or usb devices or cd/dvd and then show them in left panel in COMPUTER category.
i want my nautilus come back to previous mode.

---

### Post by amerllica on 2012-10-20
all of you pee off
i install ubuntu 12.10 and everything is ok

:guitar:

---

