---
title: "mtools error"
date: 2008-05-29
forum: General Help
---

### Post by johnconnor on 2008-05-29
Hello everyone !

I'd like to hide some files on my memory card (fat32) for windows users. I wanted to use the *mattrib +h* command from mtools, but I get this message:

> Can't open /dev/fd0: No such file or directory
Cannot initialize 'A:'

Here is my /etc/mtools.conf file:

> # Debian default mtools.conf file.
# "info mtools" or "man mtools.conf" for more detail.

# # Linux floppy drives
drive a: file="/dev/fd0" exclusive
drive b: file="/dev/fd1" exclusive

# # First SCSI hard disk partition
# drive c: file="/dev/sda1"

# # First IDE hard disk partition
# drive c: file="/dev/hda1"

# # dosemu hdimage.
drive m: file="/var/lib/dosemu/hdimage.first" partition=1 offset=128

# # dosemu floppy image
drive n: file="/var/lib/dosemu/fdimage"

# # SCSI zip disk
# drive z: file="/dev/sda4"

# # uncomment the following line to display all file names in lower
# # case by default
# mtools_lower_case=1

I changed it this way but it did not solve my problem:

> # Debian default mtools.conf file.
# "info mtools" or "man mtools.conf" for more detail.

# # Linux floppy drives
**#** drive a: file="/dev/fd0" exclusive
**#** drive b: file="/dev/fd1" exclusive

# # First SCSI hard disk partition
**drive a: file="/dev/sda1"**

# # First IDE hard disk partition
# drive c: file="/dev/hda1"

# # dosemu hdimage.
**#** drive m: file="/var/lib/dosemu/hdimage.first" partition=1 offset=128

# # dosemu floppy image
**#** drive n: file="/var/lib/dosemu/fdimage"

# # SCSI zip disk
# drive z: file="/dev/sda4"

# # uncomment the following line to display all file names in lower
# # case by default
# mtools_lower_case=1

Do anyone know how to solve this problem?

---

### Post by KingTermite on 2008-05-29
First, how are you using the command to attrib the file(s) in the first place?

Are you trying to do it file by file, or using wild cards or how?

---

### Post by johnconnor on 2008-05-29
The file I try to hide is */media/sdqtek/test.txt* so the command I use is:

*$ mattrib +h /media/sdqtek/test.txt*

and I get this:

> Can't open /dev/fd0: No such file or directory
Cannot initialize 'A:'

---

### Post by johnconnor on 2008-05-31
Any idea?

---

