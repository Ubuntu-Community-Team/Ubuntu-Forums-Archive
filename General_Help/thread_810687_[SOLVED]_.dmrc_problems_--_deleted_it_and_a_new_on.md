---
title: "[SOLVED] .dmrc problems -- deleted it and a new one is NOT generated"
date: 2008-05-28
forum: General Help
---

### Post by fuzzyl0g1c on 2008-05-28
So I have a strange problem here. I was having problems with my .dmrc permissions (got a warning when logging in) so I tried deleting it (hoping it would be re-generated) and it won't come back. ls -l .dmrc in the home directory returns file not found everytime I reboot. I've got home on it's own partition, and I'm mounting it in fstab:

```

  GNU nano 2.0.7              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1befa5ff-a6fd-4f19-876d-87a2d26a36ca /               ext3    relatime,erro$
# /dev/sda5
UUID=03486dfb-ed10-4ebb-8390-06f85a0376cb none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3        /home ext3 nodev,nosuid 0 2

```

I would just make a new .dmrc, but I couldn't find what exactly needed to be in it? Any suggestions :confused:? Thanks!

---

### Post by fuzzyl0g1c on 2008-05-29
bump. :(

---

### Post by fuzzyl0g1c on 2008-05-29
Nevermind, I figured it out. If anybody else has this problem just create a new .dmrc file (blank) with the proper permissions.

[http://ubuntuforums.org/showpost.php?p=2427423&postcount=2](http://ubuntuforums.org/showpost.php?p=2427423&postcount=2)

---

