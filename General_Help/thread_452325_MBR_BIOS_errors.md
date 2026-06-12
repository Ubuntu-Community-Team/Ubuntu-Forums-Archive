---
title: "MBR/ BIOS errors"
date: 2007-05-23
forum: General Help
---

### Post by spoz on 2007-05-23
I spent quite a wile last week downloading the basic ubuntu version, installed fine but when I went to boot I got serveral errors appear. I thought maybe its just due to that ISO so I downloaded ubuntustudio but yet again, the same errors...

```

Warning: MBR Cylinders (30402) is not equal to the BIOS one (16383).

Warning: MBR total sectors (488408130) is greater than the BIOS one (488.97168).
Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit

ERROR 17: File not found

```

I've defragged all hard drives but still this is happening, anyone able to shed any light on this.
o.O

---

### Post by ago on 2007-05-23
Unzip the content of the following file and replace c:\grldr

[http://ubuntuforums.org/showpost.php?p=2705291&postcount=53](http://ubuntuforums.org/showpost.php?p=2705291&postcount=53)

---

### Post by spoz on 2007-05-23
i'll try that now

just after posting this thread I read a few others and tried the minefield version and sucsess! the errors were still there but it continued on to the installer :D

**but**... the installer finished and rebooted and now ontop of them errors I get 2 new ones

```

non-resident attribute list not supported

No $INDEX_ROOT

```

/me sighs...:(

---

### Post by ago on 2007-05-23
If you are using the latest grldr, see the end of the sticky thread about grldr, there is a bean123 post with diagnostic commands (and my reply), add your results as well.

---

### Post by spoz on 2007-05-23
just added the newest grldr edition and it works perfectly, thanks for your help dude :D <3

---

