---
title: "On the (output of the) command 'badblocks'"
date: 2013-06-13
forum: General Help
---

### Post by Macamba on 2013-06-13
Hi,

My harddisk and me have some issues. The other day I performed a badblocks on it, as in:
```

sudo badblocks -sv -o badblocks_output.txt /dev/sdb1

```

In this case /dev/sdb1 had no problems. On another partition I got a file with 274 badblocks. So, what do I do with that file?

TIA,
Macamba

Edit. The program ended with
```

Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```
Does anyone know what kind of errors are meant with the (0/0/0 errors)?

---

### Post by BioHazardTM on 2013-06-13
From: [https://wiki.archlinux.org/index.php/Badblocks](https://wiki.archlinux.org/index.php/Badblocks)

[COLOR=#000000][FONT=sans-serif]The means of [/FONT][/COLOR]0/0/0[COLOR=#000000][FONT=sans-serif] errors is <number of read errors>/<number of write errors>/<number of corruption errors>.[/FONT][/COLOR]

---

### Post by Macamba on 2013-06-14
Thanks

---

