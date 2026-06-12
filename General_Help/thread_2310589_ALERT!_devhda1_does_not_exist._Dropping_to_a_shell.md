---
title: "ALERT! /dev/hda1 does not exist. Dropping to a shell!"
date: 2016-01-20
forum: General Help
---

### Post by Guy_Ouahnon on 2016-01-20
Hi All,

I have an Ubuntu machine kernel 2.6.15-57-server (that i don't know much about) running on ESX.
The machine holds critical data and i wish to retrieve it or to somehow fix the machine.

After a power failure this guest does not start normally and i get the following error:
[COLOR=#0000ff]ALERT! /dev/hda1 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

[/COLOR]Can someone offer any help on the matter?
What can i do in this situation?

Thanks for any helpfull reply.

---

### Post by Bashing-om on 2016-01-20
Guy_Ouahnon; Whoa ....

Kernel "  2.6.15-57-server " goes back to release 6.06 - dapper drake - , I can not realize any value in trying to fix this install as it has been out of support for many years.

What we can do is concentrate on copying off that needed data .
So, what are we working with ? raid - on a server, quite possible ?

Boot up a liveDVD ( desktop install medium, any release)
and
Show us:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

``` 
The outputs between code tags, please
we identify the partitions, mount the partitions that contain your data, and copy the data off.

[INDENT][INDENT]least ways, that is my thought
[/INDENT][/INDENT]

---

