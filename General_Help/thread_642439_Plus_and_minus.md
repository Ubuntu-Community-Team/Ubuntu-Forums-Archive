---
title: "Plus and minus"
date: 2007-12-16
forum: General Help
---

### Post by ksonic1055 on 2007-12-16
Can anyone tell me what the pluses and minuses in this mean? Im editing my Nvidia driver and i was told to make the following changes to Nvidia.py:

```
--- nvidia.py_orig 2007-10-08 22:32:08.000000000 -0400
+++ nvidia.py_new 2007-10-09 16:34:39.000000000 -0400
@@ -38,21 +38,22 @@
         # compiz does not work otherwise
         self.xorg_conf.getSections('Screen')[0].defaultdepth = 24

 class LegacyNvidiaDriver(NvidiaDriver):
     is_handler = True

     name = "nvidia_legacy"

     def __init__(self, module):
         NvidiaDriver.__init__(self, module, "nvidia-glx-legacy",
- {"AllowGLXWithComposite": "True", "NoLogo": "True"})
+ {"AllowGLXWithComposite": "True", "NoLogo": "True",
+ "UseEdidFreqs": "True"})

     def description(self):
         return _("NVIDIA accelerated graphics driver (legacy cards)")

 class NewNvidiaDriver(NvidiaDriver):
     is_handler = True

     name = "nvidia_new"

     def __init__(self, module):
```

Does that mean I should remove lines with a minus in front and add the lines with pluses in front? Or should i just copy that segment pluses and all?


Thanks

---

### Post by geraldm on 2007-12-16
The file is a patch to a source package/file.  It is usually applied using the command patch.
Details are in the manpage for patch.  Use the name of the file for "{DIFF-FILENAME}"
```

patch -p0 -i {DIFF-FILENAME}

```
After the patch is applied, the lines that start with one "-" are removed; the lines that start with one"+" are to be added.  The first two lines are names for the two files that have differences.  The third line is information on the lines that are different.  The remaining lines are the context to identify the place where the changes are to be made.  The differences between the two files are created by the command diff (and its options)

Gerald

---

### Post by ksonic1055 on 2007-12-16
Ok thanks. I think Ill use that information to manually edit it. Im new to ubuntu and that seems easier.

---

