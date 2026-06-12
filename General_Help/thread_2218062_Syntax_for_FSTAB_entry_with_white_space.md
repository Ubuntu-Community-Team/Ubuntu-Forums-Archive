---
title: "Syntax for FSTAB entry with white space"
date: 2014-04-19
forum: General Help
---

### Post by jdallara on 2014-04-19
Hello,

I need to have the following entry in my etc/fstab file:

```
# mount VM disks partition under /home/jon
UUID=07e9092e-7e43-45fa-a0a9-5bf878f62bfe    "/home/jon/VirtualBox VMs"    
ext4    defaults    0    2
```

I have tried single quotes, double quotes, back slash, but I haven't gotten it to mount at boot.  I can manually mount it using:

root@jon-desktop2:~# mount UUID=07e9092e-7e43-45fa-a0a9-5bf878f62bfe /home/jon/VirtualBox\ VMs

Any ideas on how to escape the white space?

Thanks,

Jon.

---

### Post by steeldriver on 2014-04-19
Try using octal escape sequences for the spaces (\040 = decimal 32 = ASCII space)

```

# mount VM disks partition under /home/jon
UUID=07e9092e-7e43-45fa-a0a9-5bf878f62bfe    /home/jon/VirtualBox[COLOR=#0000ff]\040[/COLOR]VMs    ext4    defaults    0    2

```

Also AFAIK the entry must be all on one line (not split before the 'ext4' as in your example)

---

### Post by SeijiSensei on 2014-04-19
You might consider just deleting the space in the name "VirtualBox VMs".  Then open the VirtualBox manager and use File > Preferences > General to change the name of the directory to match.

---

### Post by warp99 on 2014-04-19
From the FSTAB man pages:

              The second field (fs_file).
              
              This  field  describes  the mount point for the filesystem.  For
              swap partitions, this field should be specified  as  `none'.  If
              the name of the mount point contains spaces these can be escaped
              as `\040'.

---

### Post by jdallara on 2014-04-19
Doh!  Forgot about octal.  Thought  that went out in the 90's ;)

Thanks All,

Jon.

---

