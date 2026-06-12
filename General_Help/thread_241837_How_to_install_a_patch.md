---
title: "How to install a patch"
date: 2006-08-22
forum: General Help
---

### Post by cssutto on 2006-08-22
I see all of these patches to add features to various packages.

So how do I install a patch?

The particular one that interests me is a side bar patch for mutt.

CSSJR

---

### Post by croak77 on 2006-08-22
Usually you patch the source code of a program.

---

### Post by peabody on 2006-08-22
> **cssutto said:**
> I see all of these patches to add features to various packages.

So how do I install a patch?

The particular one that interests me is a side bar patch for mutt.

CSSJR

Patches are applied to source code.  Patches are just text files in a format known as diff (context format I believe) which shows the differences in text in the new version and old version.

You would get the source code of the software in question and then untar/unzip it.  Then from the command line you would use patch.  Unfortunately how to invoke patch for different patches may be different, but this is typically how they are applied.  From within the folder just above the source folder, you would run:

patch -p0 < (relative or absolute path to patch file)

If you see a series of lines print to the screen saying something like hunk succeeded, the patch has been successfully applied and you can now try to compile and install the software from source.

---

