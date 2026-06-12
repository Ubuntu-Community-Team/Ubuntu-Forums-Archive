---
title: "Determining (correct) disk geometry"
date: 2006-08-19
forum: General Help
---

### Post by RikoW on 2006-08-19
Hi all,

how to you determine the correct disk geometry? I read somewhere, that the geometry reported bu 2.6 kernels is wrong, so:

```
> hdparm -g /dev/hda

/dev/hda:
 geometry     = 65535/16/63, sectors = 156301488, start = 0

```

is correct or wrong for a 80 GB disk?

Why do I care?

I have VMware workstation running a physical install of XP. When I run something with lots of HD access, I get /dev/hda I/O errors. I read in some forum, that might be due to different disk geometries assumed by the host and the guest. Indeed, when I look at the disk description file of the of VMware, I find 2 (!) other geometries:

```
ddb.geometry.cylinders = "16383"
ddb.geometry.heads = "16"
ddb.geometry.sectors = "63"
ddb.geometry.biosCylinders = "1024"
ddb.geometry.biosHeads = "255"
ddb.geometry.biosSectors = "63"
ddb.adapterType = "ide"
ddb.toolsVersion = "6404"

 
```

Big question: Which is the correct one? So which one I should change?

Thanks and cheers,

               Riko

---

### Post by Ocxic on 2006-08-19
the best way to get your disk geometry is to look on the label on your hard drive, it's ussually there. unfourtunaly it requires you to actually pull the drive out of your comp.

---

### Post by RikoW on 2006-08-19
Not quit so easy :) ... maybe because it's a laptop disk? Anyway, via the model number and google I got the design geometry. Turns out, it's NOT the one Linux reports but the one shown for the disk of the virtual machine.

As far as I know, I can pass the disk geometry as boot parameter to the kernel via 

```

hda=16383,16,63
```

Does Linux care at all about the geometry? Can I trash something serious, if I pass the disk geometry to the kernel?

Thanks,

          Riko

---

