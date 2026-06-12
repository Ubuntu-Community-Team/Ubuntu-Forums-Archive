---
title: "How do I mount /dev/hdc1 with write permissions?"
date: 2005-10-23
forum: General Help
---

### Post by jang on 2005-10-23
Hello there.  I have a sata hard drive that I remove and connect regularly.  But when I had the chance to mount it, it is always in read only mode.

Details are as follows:

/dev/hdc1 sata hdd fat32 partition

How do I mount it manually, and also, please show me how to mount it in /etc/fstab.  As usual, my mounted results are read only.

Thanks.

---

### Post by La1nE on 2005-10-23
This is what ubuntuguide.org told me;

sudo mount /dev/hdc1 /etc/fstab/ -t vfat -o iocharset=utf8,umask=000

Havn't tried it myself, but it seems ok. 

scource : [http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by Emerzen on 2005-10-23
Mount:

[B]sudo mount /dev/hdc1 /anyemptydirecotry -t vfat
[/B]

To add it to fstab:

[B]sudo mkdir /media/externaldrive
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/B]

Add the following line:

**/dev/hdc1       /media/externaldrive  vfat    iocharset=utf8,umask=000   0       0**

I'm assuming the external drive is FAT32 formatted?  If it's ext3/2, it's a minor mod, but lemme know.

---

### Post by jang on 2005-10-24
Hello there.  Thank you for your replies.  My question is where do you get these:

" iocharset=utf8,umask=000 0 0"  I can't always remember on how to mount them without any help.  Is there a code or guidebook on how to do this so I can remember it all the time?  I don't know what they mean.

---

### Post by stoeptegel on 2005-10-24
umask:
```
SYNOPSIS

umask [-S] [mode]
DESCRIPTION

umask sets the file mode creation mask of the invoking process to the given mode. You can specify the mode in any of the formats recognized by chmod; see chmod for more information.

The file mode creation mask (often called the umask) determines the default permissions for any file created by the process. For example, a file created by the create command has the permissions specified by the umask unless the create command specifies explicit permissions.

Calling umask without a mode argument displays the current umask.
Options

-S 

    displays the umask in a symbolic form:

u=perms,g=perms,o=perms

    giving user, group and other permissions. Permissions are specified as combinations of the letters r (read), w (write) and x (execute).

```


iocharset=utf8:
I think that have something to do with the filesystem, i wanna know this one too.:)

---

### Post by La1nE on 2005-10-24
utf8 is a character set. 

for example, on irc i use ISO-8859-15, since i have special charakters (&#229;&#228;&#246;)

If you want to know more about the different charakter-sets, just look around in the forum. ;)

---

### Post by stoeptegel on 2005-10-24
I know it's character set, i learned that i the past when i did some errors with BOM enabled utf-8 php files. But i guess i wanna know what it has got to do with a filesystem and what it carries out in fstab, poke me if someone knows please.

EDit
oeps, i sort of hijacked this topic, sorry :-$

---

### Post by csscll on 2005-10-24
[QUOTE=jang]Hello there.  Thank you for your replies.  My question is where do you get these:

" iocharset=utf8,umask=000 0 0"  I can't always remember on how to mount them without any help.  Is there a code or guidebook on how to do this so I can remember it all the time?  I don't know what they mean.[/QUOTE]

Hello, umask is very useful, if you know what those numbers mean. 

 umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

    * character '0': Indicates that this is an octal number, not decimal.
    * first digit: owner user permissions
    * second digit: owner group permissions
    * third digit: world permissions (every other user on the system) 

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * - 
2 | * - * 
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: 

[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS))

---

### Post by jang on 2005-10-25
stoeptegel- go ahead, I don't mind.  I'm also wondering what charsets do to it.

csscll- thanks very much.  I usually don't set permissions or anything since i'm the only one using the PC.  That means everytime I do umask, just do a 0000.  I'll read about the howto you provided.  Thanks.

---

