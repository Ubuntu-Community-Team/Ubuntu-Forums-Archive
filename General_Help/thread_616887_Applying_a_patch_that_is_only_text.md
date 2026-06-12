---
title: "Applying a patch that is only text"
date: 2007-11-18
forum: General Help
---

### Post by jebrum on 2007-11-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152818](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152818) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm trying to patch dmraid to fix a bug mentioned here: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152818](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152818)

The patch is just code. Any help on how to apply it will be appreciated.

Here is the code:

diff -urN 1.0.0.rc13.orig/lib/format/ataraid/jm.c 1.0.0.rc13/lib/format/ataraid/jm.c
--- 1.0.0.rc13.orig/lib/format/ataraid/jm.c	2007-10-15 10:53:11.000000000 +0100
+++ 1.0.0.rc13/lib/format/ataraid/jm.c	2007-10-15 10:53:07.000000000 +0100
@@ -28,10 +28,16 @@
 	size_t len;
 	struct jm *jm = META(rd, jm);
 	char buf[2], *ret, *name = (char *) jm->name;
+	char buf0[JM_NAME_LEN+1] = { '\0' };
+	size_t i = JM_NAME_LEN-1;
 
-	/* Name always 0 terminated ? */
-	if ((len = strlen(name)) > JM_NAME_LEN)
-		len = JM_NAME_LEN;
+	/* Sanitize name, make sure it's null terminated */
+	strncpy(buf0, jm->name, JM_NAME_LEN);
+	while (i!=0 && buf0[i]==' ') {
+		buf0[i]='\0';
+		--i;
+	}
+	len = strlen(buf0);
 
 	len += sizeof(HANDLER) + 2;
 	if (jm->mode == JM_T_RAID01)
@@ -43,7 +49,7 @@
 		else
 			*buf = 0;
 
-		sprintf(ret, "%s_%s%s", HANDLER, name, buf);
+		sprintf(ret, "%s_%s%s", HANDLER, buf0, buf);
 	}
 
 	return ret;

---

### Post by ajmorris on 2007-11-18
Not entirely sure what it is you are trying to patch, as the link you specified does not exist, or at least i cant access it. However, generally one patches a file via this command (whilst in the directory of the source)

```
  patch -p0 < patch-file-name-here
```

---

