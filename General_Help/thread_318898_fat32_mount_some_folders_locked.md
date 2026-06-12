---
title: "fat32 mount some folders locked"
date: 2006-12-14
forum: General Help
---

### Post by antiigrav on 2006-12-14
hi,

i mounted a fat32 partition on a separate hdd with full permissions.

however, only some folders amoung many are displayed with a padlock icon, and i do not have write permissions.

i cant see any reason except maybe they have more files in them than the others? they are not 'read only' under windows.

how can i enable permissions on these folders please?

thanks. (very new linux user.)

---

### Post by taurus on 2006-12-14
Do you mount it by hand (from a terminal) or do you mount it through /etc/fstab?  If you mount it by hand, can you include it here; otherwise, paste this command here if you use /etc/fstab to mount it...

```
cat /etc/fstab
```

---

### Post by antiigrav on 2006-12-14
hi and thanks.

i use fstab with this line i found in a tutorial:

```
/dev/sdb1    /media/hdd1 vfat iocharset=utf8,umask=000 0 0
```

From another tutorial, i added a script 'open as administrator' to Nautilus, and if i use this to open the mount point the problem goes away.

so i need to give my standard user-login permissions for every level below the mount point? not sure how...

(i still dont see why only some folders are locked tho)

---

