---
title: "rename weirdness"
date: 2008-06-28
forum: General Help
---

### Post by simply seth on 2008-06-28
what in the world is up with not being able to change filenames ?! 

[i]
 rename 's/\.wav$/\.WAV/'  fnkynassau.wav 
fnkynassau.wav not renamed: fnkynassau.WAV already exists
[/i]
and no, there is not a file named  fnkynassau.WAV

[i] mv fnkynassau.wav fnkynassau.WAV
mv: `fnkynassau.wav' and `fnkynassau.WAV' are the same file
[/i]

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

---

### Post by jocko on 2008-06-28
Let me guess... The file named fnkynassau.wav is on an ntfs or fat file system?
Those file systems are not case sensitive, so you can't rename a file to the same name with different case. Rename the file to something else first.

---

### Post by geirha on 2008-06-28
Is this on an NTFS or FAT filesystem? If so, they have this weird case issue. The only way around it as far as I know, is to rename it with a different name first, then rename it back with to the old file with capital WAV.

---

