---
title: "fstab:  Can you help with a quick questions about editing fstab ?"
date: 2007-06-08
forum: General Help
---

### Post by brjoon1021 on 2007-06-08
Here is an entry in my fstab

/dev/hdg2 /mnt/win_g vfat user,exec,rw,noauto,iocharset=iso8859-1,codepage=850,umask=0 0 0
# /dev/hdi1, size=1542177, type=7: NTFS (primary)

I want to comment this entry out so that it is not read during boot. Where does the "#" go ? The first line or the second? If you read this and know the answer , please respond, even a "first" or "second" is enough
Thanks,
b

---

### Post by EndPerform on 2007-06-08
The second entry is already commented out.  You'd put # in front of the first line, so it would look like this:

```

# /dev/hdg2 /mnt/win_g vfat user,exec,rw,noauto,iocharset=iso8859-1,codepage=850,umask=0 0 0
# /dev/hdi1, size=1542177, type=7: NTFS (primary)

```

---

### Post by brjoon1021 on 2007-06-08
************  Solved ********************************************

Thanks!

---

### Post by stami on 2007-06-08
Hi,
the second line is already commented and however it is in a strange format. I think if you uncomment that line you'll get an error. If you do not want hdg2 to be mounted at boot you to put a # at the beginning of the line.
So your new line in fstab should be like this:

```

#/dev/hdg2 /mnt/win_g vfat user,exec,rw,noauto,iocharset=iso8859-1,codepage=850,umask=0 0 0

```

---

