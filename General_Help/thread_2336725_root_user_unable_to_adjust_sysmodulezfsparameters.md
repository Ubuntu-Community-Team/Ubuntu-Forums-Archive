---
title: "root user unable to adjust /sys/module/zfs/parameters"
date: 2016-09-10
forum: General Help
---

### Post by MasterCATZ on 2016-09-10
root@aio:/sys/module/zfs/parameters# echo 25 > /sys/module/zfs/parameters/zio_taskq_batch_pct
bash: /sys/module/zfs/parameters/zio_taskq_batch_pct: Permission denied


any idea why as root user I can not change settings ? 


root@aio:/sys/module/zfs/parameters# modprobe zfs zio_taskq_batch_pct=25
root@aio:/sys/module/zfs/parameters# cat /sys/module/zfs/parameters/zio_taskq_batch_pct
75



any idea's ?

---

### Post by Keith_Helms on 2016-09-10
Never mind.  Don't know what I was thinking when I wrote my reply.

---

### Post by MasterCATZ on 2016-09-30
[COLOR=#333333][FONT=-apple-system]looks like you have to alter the source code and change the permissions from 0444 to 0644

alternatively apparently 
/etc/modprobe.d/zfs.conf
 

The following patch will make it writable but you must set it after module load and before pool import.[/FONT][/COLOR]
[COLOR=#333333][FONT=-apple-system][COLOR=#0086B3]diff --git a/module/zfs/spa.c b/module/zfs/spa.c[/COLOR]
index c7cfe6e..d76e011 100644
[COLOR=#BD2C00]--- a/module/zfs/spa.c[/COLOR]
[COLOR=#55A532]+++ b/module/zfs/spa.c[/COLOR]
[COLOR=#795DA3]**@@ -6907,7 +6907,7 @@**[/COLOR] module_param(spa_load_verify_data, int, 0644);
 MODULE_PARM_DESC(spa_load_verify_data,
        "Set to traverse data on pool import");

[COLOR=#BD2C00]-module_param(zio_taskq_batch_pct, uint, 0444);[/COLOR]
[COLOR=#55A532]+module_param(zio_taskq_batch_pct, uint, 0644);[/COLOR]
 MODULE_PARM_DESC(zio_taskq_batch_pct,
        "Percentage of CPUs to run an IO worker thread");[/FONT][/COLOR]

---

