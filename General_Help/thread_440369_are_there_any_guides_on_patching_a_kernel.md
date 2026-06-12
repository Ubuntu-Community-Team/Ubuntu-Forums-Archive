---
title: "are there any guides on patching a kernel?"
date: 2007-05-11
forum: General Help
---

### Post by grahams on 2007-05-11
I'd like to install a patch. 

I have the patch and I think I know how to add the patch to the source. But I'm a little nervious about patching a kernel without reading up on this.

thanks in advance

---

### Post by heimo on 2007-05-11
You apply a patch by using patch. :) Instructions:
[http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)

---

### Post by grahams on 2007-05-11
Thanks for the quick reply

I assumed I needed to patch the source and then recompile. Does patch work on the binaries?

This is the patch I'm hoping to install

```
===== drivers/usb/storage/transport.c 1.145 vs edited =====
--- 1.145/drivers/usb/storage/transport.c       Tue Aug  3 10:17:59 2004
+++ edited/drivers/usb/storage/transport.c      Wed Aug 18 11:48:27 2004
@@ -1054,8 +1054,10 @@
 
        /* try to compute the actual residue, based on how much data
         * was really transferred and what the device tells us */
-       residue = min(residue, transfer_length);
-       srb->resid = max(srb->resid, (int) residue);
+       if (!(us->flags & US_FL_IGNORE_RESIDUE)) {
+               residue = min(residue, transfer_length);
+               srb->resid = max(srb->resid, (int) residue);
+       }
 
        /* based on the status code, we report good or bad */
        switch (bcs->Status) {
===== drivers/usb/storage/unusual_devs.h 1.144 vs edited =====
--- 1.144/drivers/usb/storage/unusual_devs.h    Fri Aug  6 03:59:29 2004
+++ edited/drivers/usb/storage/unusual_devs.h   Wed Aug 18 11:47:06 2004
@@ -265,6 +265,13 @@
                US_SC_8070, US_PR_BULK, NULL,
                US_FL_FIX_INQUIRY ),
 
+/* Reported by Iacopo Spalletti <avvisi@spalletti.it> */
+UNUSUAL_DEV(  0x052b, 0x1807, 0x0100, 0x0100, 
+               "Tekom Technologies, Inc",
+               "300_CAMERA", 
+               US_SC_DEVICE, US_PR_DEVICE, NULL,
+               US_FL_IGNORE_RESIDUE ),
+
 /* This entry is needed because the device reports Sub=ff */
 UNUSUAL_DEV(  0x054c, 0x0010, 0x0106, 0x0450, 
                "Sony",
===== drivers/usb/storage/usb.h 1.60 vs edited =====
--- 1.60/drivers/usb/storage/usb.h      Tue Jul 20 19:30:35 2004
+++ edited/drivers/usb/storage/usb.h    Wed Aug 18 11:46:58 2004
@@ -73,6 +73,7 @@
 #define US_FL_SCM_MULT_TARG   0x00000020 /* supports multiple targets      */
 #define US_FL_FIX_INQUIRY     0x00000040 /* INQUIRY response needs faking   */
 #define US_FL_FIX_CAPACITY    0x00000080 /* READ CAPACITY response too big  */
+#define US_FL_IGNORE_RESIDUE  0x00000100 /* reported residue is wrong      */
 
 /* Dynamic flag definitions: used in set_bit() etc. */
 #define US_FLIDX_URB_ACTIVE    18  /* 0x00040000  current_urb is in use  */

```

---

### Post by heimo on 2007-05-11
That's source patch, and it's the way it's done in Linux world. So yes, you apply it to Linux source tree, and you need to apply it to the exact version that this patch was made for. Do you have instructions on the site you got the patch from?

---

### Post by grahams on 2007-05-11
Unfortunately I don't have any instructions. 

The patch was made against 2.6.11 and was proposed to be submitted into the kernel, but it doesn't look like it did as I get exactly the same issue with a badly behaving usb to ide converter that fails with I/O errors under 2.6.17 (thats works fine with a 2.4.xx kernel with the older usb stack). I submitted this as a bug months ago but no progress was made.

I was hoping I could patch my 2.6.17 kernel and see if it fixes the issues.

[https://launchpad.net/bugs/81059](https://launchpad.net/bugs/81059)

---

### Post by heimo on 2007-05-11
You could try to get exact same vanilla version of Linux, patch it, configure, make, make modules, make install... After patching it should be same process as compiling and installing any kernel.
[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by grahams on 2007-05-11
is there no way I can use my current kernel as a base?

---

### Post by heimo on 2007-05-11
> **grahams said:**
> is there no way I can use my current kernel as a base?

I'm afraid not. Not easy way, I'd guess. You can try... But it may require some work. Ubuntu kernels are patched already, so they differ from vanilla kernels, and taking whole different version with a set of patches and applying a patch for another kernel... You'd be lucky if it works.

---

### Post by grahams on 2007-05-11
Thanks a lot for the advise. 

I think I'll avoid the pain a buy a different converter.

---

### Post by heimo on 2007-05-11
I looked at Ubuntus Linux 2.6.20 source and at least most of the patch seems to be there, I didn't see the last part - the one single define line(*. Actually, shouldn't be too complicated to apply this patch manually, but I have no idea what it does, what it should fix and if it fixes problem that you've with your adapter.

*) I didn't look too closely, I'm almost asleep, I may have missed something.

---

