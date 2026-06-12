---
title: "How to Load hda1/hda5 and hdb2"
date: 2005-07-10
forum: General Help
---

### Post by Mic on 2005-07-10
My pc have been using with Knoppix and seems to be okay, all windows partition can be easily located with Konqueror and all loads well.

Just tried the Ubuntulinux LiveCD and do not know where to find my harddisk. I am totally lost with GNOME (or maybe Ubuntu). Even the file manager did not show my harddisk.

Any suggestions?

---

### Post by mtron on 2005-07-10
To mount Windows NTFS partition (assuming that Winxp is istalled on the first patition of the first IDE HD) reaD ONLY

Open terminal & type 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

To unmount Windows NTFS partition

sudo umount /media/windows/

and for Fat32 partitons (READ / WRITE)
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

I hope this works also for the live cd, but for a hd install that's it.

---

### Post by Mic on 2005-07-11
[QUOTE=mtron]To mount Windows NTFS partition (assuming that Winxp is istalled on the first patition of the first IDE HD) reaD ONLY

Open terminal & type 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

To unmount Windows NTFS partition

sudo umount /media/windows/

and for Fat32 partitons (READ / WRITE)
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

[/QUOTE]


Hi mtron, 

many thanks for the advise, I had just dive in and installed Ubuntu, 
appreciate if you can elaborate a bit on these

nls=utf8
iocharset=utf8
umask=0222 and 0000

why is there a need for these different parameters.

Thanks again for the advice.

---

### Post by brim4brim on 2005-07-11
[QUOTE=Mic]Hi mtron, 

many thanks for the advise, I had just dive in and installed Ubuntu, 
appreciate if you can elaborate a bit on these

nls=utf8
iocharset=utf8
umask=0222 and 0000

why is there a need for these different parameters.

Thanks again for the advice.[/QUOTE]
 I'm not sure about the others but I think umask is permissions.  You have to set read only permissions for windows NTFS partitions.

If you follow the links in my sig you'll find some how to's for getting it setup on an installed version of Ubuntu so it mounts automatically on boot.

---

### Post by darkmatter on 2005-07-12
[QUOTE=Mic]I had just dive in and installed Ubuntu, 
appreciate if you can elaborate a bit on these

nls=utf8
iocharset=utf8
umask=0222 and 0000

why is there a need for these different parameters.

Thanks again for the advice.[/QUOTE]

nls=utf8 sets the National Language Support to utf8 encoding.

iocharset=utf8 sets the input/output character set to utf8 encoding.

The utf8 [(Unicode Tranformation Format)8] is the character encoding model to be used for accessing/writing/displaying information. 
For more info on unicode visit [http://www.unicode.org/standard/WhatIsUnicode.html](http://www.unicode.org/standard/WhatIsUnicode.html)

Basically, it's a way of standardizing the the encoding your computer uses to store documentation.

---

### Post by Mic on 2005-07-12
[QUOTE=darkmatter]nls=utf8 sets the National Language Support to utf8 encoding.

iocharset=utf8 sets the input/output character set to utf8 encoding.

The utf8 [(Unicode Tranformation Format)8] is the character encoding model to be used for accessing/writing/displaying information. 
For more info on unicode visit [http://www.unicode.org/standard/WhatIsUnicode.html](http://www.unicode.org/standard/WhatIsUnicode.html)

Basically, it's a way of standardizing the the encoding your computer uses to store documentation.[/QUOTE]


Whoa !!!  that's deep stuff to me  :-P 

does that means mtron's advice is the "standard" way that everyone is using, just curious

---

### Post by darkmatter on 2005-07-12
Yes, utf8 is the generally accepted format.

---

### Post by skill_guy on 2005-07-30
when i try this in the root terminal i get this:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
in some cases useful info is found in syslog - try
dmesg   tail or so

im pretty stuck and a linux newbie:)

---

