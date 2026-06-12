---
title: "[SOLVED] Permission and Ownership problems with DVD-RW - New issue"
date: 2007-08-23
forum: General Help
---

### Post by Statik on 2007-08-23
Hi all,

I recently had an issue with my system where I entered an incorrect chown command and had the ownership for a ton of files set to a particular user, instead of root. I've been cleaning it up, but one problem I haven't fixed yet is the DVD-RW.

Before this happened, when I placed a DVD in the drive, it was mounted automatically and started to play. Now, nothing happens. If I open Places->Computer and click on the drive, I get an error that says "must be superuser to use mount" or something like that. Which files should I be looking at and what should be their ownership/permission to reset this back to normal?

Any help, other than 'just reinstall the system' :) is appreciated.

Statik

---

### Post by Statik on 2007-08-24
Followup information for you all:

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=77e52f93-1d9f-44ca-8b1c-c6d15f57b984 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d5b37a50-2e3a-4e21-927e-83c84781ef4e /home           ext3    defaults        0       2
# /dev/sda5
UUID=10e8681f-c8af-49e9-bb5b-8f79358bd72e none            swap    sw              0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user,noauto   0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /home/statik/share vfat    defaults,auto,utf8,umask=0000,gid=46    0    2

```

/media
```

drwxr-xr-x  4 root root 4096 2007-08-24 13:51 .
drwxr-xr-x 21 root root 4096 2007-05-28 16:38 ..
lrwxrwxrwx  1 root root    6 2007-03-02 12:08 cdrom -> cdrom0
drwxrwxrwx  2 root root 4096 2007-03-02 12:08 cdrom0
lrwxrwxrwx  1 root root    7 2007-03-02 12:08 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-03-02 12:08 floppy0
-rw-r--r--  1 root root    0 2007-08-24 13:51 .hal-mtab
--wxr-s---  1 root root    0 2007-04-21 14:16 .hal-mtab-lock

```

/dev (part of it)
```

lrwxrwxrwx  1 root root           3 2007-08-24 13:50 cdrom -> hdc
lrwxrwxrwx  1 root root           3 2007-08-24 13:50 cdrw -> hdc
crw-------  1 root root      5,   1 2007-08-24 13:51 console
lrwxrwxrwx  1 root root          11 2007-08-24 13:50 core -> /proc/kcore
drwxr-xr-x  5 root root         100 2007-08-24 13:50 disk
crw-rw----  1 root audio    14,   3 2007-08-24 13:50 dsp
lrwxrwxrwx  1 root root           3 2007-08-24 13:50 dvd -> hdc
lrwxrwxrwx  1 root root           3 2007-08-24 13:50 dvdrw -> hdc
lrwxrwxrwx  1 root root          13 2007-08-24 13:50 fd -> /proc/self/fd
brw-rw----  1 root floppy    2,   0 2007-08-24 13:50 fd0
crw-rw-rw-  1 root root      1,   7 2007-08-24 13:50 full
brw-rw----  1 root disk      3,   0 2007-08-24 13:50 hda
brw-rw----  1 root disk      3,   1 2007-08-24 13:50 hda1
brw-rw----  1 root disk      3,  64 2007-08-24 13:50 hdb
brw-rw----  1 root disk      3,  65 2007-08-24 13:50 hdb1
brwxrwxrwx  1 root cdrom    22,   0 2007-08-24 13:50 hdc
crw-rw----  1 root root    180,  96 2007-08-24 13:50 hiddev0

```

still the problem is:
```

statik@statik-desktop:/dev$ mount cdrom
mount: must be superuser to use mount

```

oh and:
```

statik@statik-desktop:~$ groups
statik adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

```

Any help appreciated

Statik

---

### Post by Statik on 2007-08-25
Well, I finally found an answer to this particular problem by asking on the Arstechnica.com forums. My old buds came through once again. Here's a cut/paste:
> Nothinman
Ars Tribunus Angusticlavius
Registered: January 14, 2000
Posts: 7561
	
Posted August 24, 2007 15:32 
  
/bin/mount has lost it's setuid bit because whenever a setuid file has it's owner changed the setuid and setgid bits are removed.

and then:
> The Shadow
Ars Centurion

Tribus: SC, USA
Registered: March 24, 1999
Posts: 719
AIM: Online Status For jimbosworldorg	
Posted August 24, 2007 17:15
  
to expand: sudo chown root /bin/mount && sudo chmod +s /bin/mount

That fixed my mount issues.

Now, I'm wondering if there is a list somewhere that I can use to figure out what other files may need this treatment. Does anyone have a list, or does anyone want to post a ls -al of their /bin directory? I'm sure there are other files deeper in the tree, but that will be a start.

Thanks,

Statik

---

### Post by dragonwings on 2007-08-25
iv got a similar problem .  as a temp fix iv made a launcher by right clicking on 
desktop and picked  the create launcher option in the command box i put the below

 sudo nautilus mount /dev/hdb /media/cdrom0

and set it to launch in terminal

---

### Post by Statik on 2007-08-25
Dragonwings: the answer I posted from ArsTechnica fixed my problem. I'm not sure where your problem lies, or the history of it, but I'd check into your /bin/mount settings using the command:

```
ls -al /bin/mount
```

This should just give you the extended listing for mount itself.

Statik

---

### Post by dragonwings on 2007-08-25
ok thats good 

not sure if you know or not but you can go to tread tools on this page and mark this as solved .

---

### Post by Statik on 2007-08-25
Nope, I didn't know that. Did it now tho, Thanks.

Statik

---

