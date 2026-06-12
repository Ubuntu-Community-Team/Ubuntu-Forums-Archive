---
title: "installing a bug patch"
date: 2012-10-25
forum: General Help
---

### Post by yanvolking on 2012-10-25
Hello Community,

Resulting from an earlier post in the "hardware section" where I ask for help in getting an acer aspire one d270 to boot with Ubuntu 12.10, one of the suggested solutions is to install a patch :

A bug report about the problem can be found here:
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1069031]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031")

Could anyone tell me how to install the patch :

```


---
hw/xfree86/common/xf86pciBus.c |   64 +++++++++++++++++++++++++++++++++++-----
 1 files changed, 56 insertions(+), 8 deletions(-)

diff --git a/hw/xfree86/common/xf86pciBus.c b/hw/xfree86/common/xf86pciBus.c
index a2c18eb..258988a 100644
--- a/hw/xfree86/common/xf86pciBus.c
+++ b/hw/xfree86/common/xf86pciBus.c
@@ -1147,14 +1147,62 @@ xf86VideoPtrToDriverList(struct pci_device *dev,
         driverList[0] = "i128";
         break;
     case 0x8086:
-        if ((dev->device_id == 0x00d1) || (dev->device_id == 0x7800)) {
-            driverList[0] = "i740";
-        }
-        else if (dev->device_id == 0x8108) {
-            break;              /* "hooray" for poulsbo */
-        }
-        else {
-            driverList[0] = "intel";
+    switch (dev->device_id)
+    {
+        /* Intel i740 */
+        case 0x00d1:
+        case 0x7800:
+            driverList[0] = "i740";
+            break;
+        /* GMA500/Poulsbo */
+        case 0x8108:
+        case 0x8109:
+            /* Try psb driver on Poulsbo - if available */
+            driverList[0] = "psb";
+            driverList[1] = "psb_drv";
+            break;
+        /* GMA600/Oaktrail */
+        case 0x4100:
+        case 0x4101:
+        case 0x4102:
+        case 0x4103:
+        case 0x4104:
+        case 0x4105:
+        case 0x4106:
+        case 0x4107:
+        /* Atom E620/Oaktrail */
+        case 0x4108:
+        /* Medfield */
+        case 0x0130:
+        case 0x0131:
+        case 0x0132:
+        case 0x0133:
+        case 0x0134:
+        case 0x0135:
+        case 0x0136:
+        case 0x0137:
+        /* GMA 3600/CDV */
+        case 0x0be0:
+        case 0x0be1:
+        case 0x0be2:
+        case 0x0be3:
+        case 0x0be4:
+        case 0x0be5:
+        case 0x0be6:
+        case 0x0be7:
+        case 0x0be8:
+        case 0x0be9:
+        case 0x0bea:
+        case 0x0beb:
+        case 0x0bec:
+        case 0x0bed:
+        case 0x0bee:
+        case 0x0bef:
+            /* Use fbdev/vesa driver on Oaktrail, Medfield, CDV */
+            break;
+        default:
+            driverList[0] = "intel";
+            break;
         }
         break;
     case 0x102b:
-- 
1.7.3.4


```I have experience in Python, php and BASH.  But I have no idea where to start with the above...

Thanks

---

### Post by mikewhatever on 2012-10-25
That's not something you can just install. The patch discribes changes to the xf86pciBus.c file found in the xserver source code. Theoretically, you could get the source code, apply the patch and then recompile. I'd advise using 12.04 instead.

---

### Post by yanvolking on 2012-10-26
Hi Mikewhatever,

I suspected that this was going to be a source code or Kernel issue, beyond my current IT abilities.  Indeed I would be better off sticking to 12.04.

Thanks

---

### Post by Riccardoc on 2012-10-29
> I suspected that this was going to be a source code or Kernel issue, beyond my current IT abilities. Indeed I would be better off sticking to 12.04.
Also, even if you manage to do it, you would end up with a fbdev driver, which means unaccelerated: no decent video, no decent games and generally really poor graphics performance.
I am staying on 12.04 and definitely would suggest you to do the same; at least you can have decent acceleration there.

---

### Post by roudy1989 on 2012-10-29
```
+        case 0x0bef:
+            /* Use fbdev/vesa driver on Oaktrail, Medfield, CDV */
+            break; +        default:
```
Shouldn't there be an assignment to driverList[] declaring the driver? Seems to be absend...
I would recommend using the LTS release. As always the new releases have to grow a bit after they have been released :-)

---

