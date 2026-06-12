---
title: "Veracrypt - character encoding  issue from windows fat32 volume"
date: 2017-09-19
forum: General Help
---

### Post by sprinterdriver on 2017-09-19
Hi.

I have installed the latest Veracrypt version on my Xubuntu laptop, and I have figured out how to use it (I'm familiar to the Veracrypt from Windows).

Have a usb drive that holds an encrypted volume. This encrypted volume is formatted as fat32 from Windows. Some of the file names on that volume contains norwegian characters (æ Æ ø Ø å Å).

The problem is after I have mounted the volume (in a folder inside my home directory) is that the file browser cannot read the norwegian characters properly.

Is there an easy fix on this problem?

Also, I noticed one major difference in the Veracrypt gui from Linux version to Windows version - where in Windows there is a list of volume letters for any mounted volumes, in Xubuntu it gives a list of sockets, numbered from one and up. What is the thing about sockets? What fifference does it makes if I choose Socket 1 instead of Socket 5 for instance - it's still mounted in an folder that would be empty unless something is mounted to that folder :-s

---

### Post by sprinterdriver on 2017-10-01
Hi - I still have no solution myself other than not using the characters "æ", "ø" and "å", but that is silly and deeply interrupt with the meaning of each folder - it's like to say to anyone that the letters "e", "u" and "t" can never be part in a file or folder name.

I have another computer running Mint, and there I have tested and laerning how to encrypt a folder, and I made it to work using mount command and a file encryption package (it's like 3 weeks ago now and I don't remembers the commands excactly but I have it all written down) - so I have thaught:

In order to decrypt files, the thing to do is to mount a directory into itself, with the file encryption package.
With that in mind, isn't it possible to somehow mount a folder or drive and specify what character encoding is used?

---

### Post by sprinterdriver on 2017-10-14
Solution seem to be found:
[https://bbs.archlinux.org/viewtopic.php?pid=1543238#p1543238](https://bbs.archlinux.org/viewtopic.php?pid=1543238#p1543238)

> [INDENT]The truecrypt volume you  created was most likely formatted as FAT32. When mounting FAT in Linux  default charset is iso8859-1, although long filenames in Windows are  stored on disk in Unicode format.

Solution: specify iocharset=utf8  in Truecrypt for Mount options (globally in preferences or for specific  volume in advanced options).


[/INDENT]


I still need to do some tests to make really sure this is the actually solution. The encrypted file container I have today I ave renamed most files in order to prevent the problem - so my little test may not have solved all problems. I will copy all files from this volume to a newly created volume that is formatted with ext4 and see if I catch some errors.

Copy all files using Thunar went without any errors regarding file names character encoding. It is very likely that the problem is solved 8-)

---

