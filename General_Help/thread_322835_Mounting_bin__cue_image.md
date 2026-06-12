---
title: "Mounting bin / cue image"
date: 2006-12-21
forum: General Help
---

### Post by Unknowndeepness on 2006-12-21
Hi there.

I have an bin / cue file, which i made to an isofile with bchunk, but when i mount it with
```
sudo mount -o loop -t iso9660 image.iso /mnt
```
it sais
```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
dmesg | tail sais:
```

[17196219.020000] Unable to identify CD-ROM format.

```

Any help?

---

### Post by po0f on 2006-12-21
Unknowndeepness,

Use [cdemu](http://cdemu.sourceforge.net/) to mount the original bin/cue.

---

### Post by Unknowndeepness on 2006-12-21
Ah, thanx, now for another problem.
After install, i mounted the image on 0, then did
```

sudo mount /dev/cdemu0 /mnt

```
and it said:
```

mount: block device /dev/cdemu0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```
what filesystem type should i use?

---

### Post by po0f on 2006-12-21
Unknowndeepness,

Taken from [here](http://cdemu.sourceforge.net/#FAQ):
```
[FONT="Courier New"]$ mount -t iso9660 /dev/cdemu/0 /mnt/cdrom[/FONT]
```

---

### Post by Unknowndeepness on 2006-12-21
Hah, aaw, i even had that site open in the background. ^^
wellwell, i did that (except i used /dev/cdemu0, since /dec/cdemu doesnt exist =), and it still complains:
```

mount: block device /dev/cdemu0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdemu0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Something wrong with my image, mabie?

---

### Post by po0f on 2006-12-21
Unknowndeepness,

Maybe, how did you create it?


This is a script I use to make BIN/CUE pairs:
```
[FONT="Courier New"]#!/bin/bash
if [[ -z "$1" ]]; then
    echo -e "Usage: `basename $0` <base_filename>\n"
    echo -e "Error: no base filename specified.\n"
    exit 1
fi

cdrdao read-cd --device ATA:1,0,0 --driver generic-mmc-raw --read-raw --datafile $1.bin $1.toc && rm $1.toc && bin2iso $1.cue -c $1.bin[/FONT]
```

You will need to install [bin2iso](http://users.eastlink.ca/~doiron/bin2iso/) first.  Download the C source file from the link labeled "bin2iso v1.9b c file" (you might have to right-click and "Save as...").  Just compile and you should be able to use it:
```
[FONT="Courier New"]$ sudo aptitude install build-essential
$ gcc -o bin2iso bin2iso19b.c
$ sudo mv bin2iso /usr/local/bin[/FONT]
```

---

### Post by Unknowndeepness on 2006-12-21
Umm, i created it with windows, a long time ago, so i dont know.
I burned the image, also, and i mean i burned the image-file (among other files) to the cd, so mabie it read it wrong or something.

I'll try to copy from the cd again, se if im more lucky then, otherwise i'll just ask someone to send the game.

Thanx for you'r help, m8. :)

---

### Post by taurus on 2006-12-21
You can use bin2iso to convert cue/bin to iso and mount it like you did before!!!

```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop **filename.iso** /mnt/iso
```

---

### Post by Unknowndeepness on 2006-12-21
Yep, thats what i did first of all, if you read my first post. :D
I used bchunk though, but it cant be much of a difference. :)

---

