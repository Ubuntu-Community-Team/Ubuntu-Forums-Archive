---
title: "Black screen boot hang (dmesg attached)"
date: 2013-01-14
forum: General Help
---

### Post by ericrcan on 2013-01-14
I have used ubuntu on and off for years, and though I do like windows 8, i decided to go back to ubuntu for my netbook. I decided on xubuntu and love it, but it is super slow at starting up. I have attached my full dmesg right after I got into the desktop, and this is where i think im having some issues. Any help would be great!

```
[    2.795911] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.795922] EXT4-fs (sda5): write access will be enabled during recovery
[    3.832683] EXT4-fs (sda5): recovery complete
[    3.848588] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  152.328689] Adding 2084860k swap on /dev/sda6.  Priority:-1 extents:1 across:2084860k 

```

[http://pastebin.com/mN28skHH](http://pastebin.com/mN28skHH)

---

### Post by hydn79 on 2013-01-14
Do you have ureadahead installed? Try removing it first.

---

### Post by ericrcan on 2013-01-14
I removed it. No fix. Now it just says that it is unable to execute it in the dmesg log too so now its longer.

```
[    2.980518] EXT4-fs (sda5): write access will be enabled during recovery
[   57.723047] EXT4-fs (sda5): recovery complete
[   57.740562] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   76.183196] init: Failed to spawn ureadahead main process: unable to execute: No such file or directory

```

---

### Post by ericrcan on 2013-01-15
i searched and cant seem to find anything to help yet. any ideas?

---

