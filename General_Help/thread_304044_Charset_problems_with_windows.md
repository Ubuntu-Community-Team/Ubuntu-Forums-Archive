---
title: "Charset problems with windows"
date: 2006-11-21
forum: General Help
---

### Post by marianom on 2006-11-21
Hi there.
I work in a development team where all my colleagues use windows and I'm the only one with Ubuntu. 
Sometimes we have problems with the charset encoding, specifically with special castilian characters (ñ, á, é, í, ó, ú, ü, etc). 
For example in the names of the documents they save instead of "ñ" I get this funny character: &#65533; 
and, in the docs I save, instead of "ñ", they see this: Ã±
I check my encoding and all seems ok (I develop with databases and I save there the characters and they're ok, also all encoding inside OO docs are ok for both of us). 
I think the problem is the windows encoding they're using: charset 1252 (WE8MSWIN1252). We investigated and it seems this is a special charset develop by windows and it seems that just windows understands it (what a suprise...)
The question now: do you guys know how can we get rid of it and replace with a valid charset that works for both of us? We searched and we can't find a right answer.

Any tips are really appreciate.

---

### Post by Average Joe on 2006-11-21
You could try the encoding UTF8. That's the Unicode Transformation Format, which is based on Unicode. And Unicode contains almost all characters there are. And the first (128 ) characters are compatible with ASCII.

---

### Post by dpm on 2006-11-21
Mariano,

try playing with the vfat driver mounting options related to encoding. As an example, here's how I mount one of my **FAT32** partitions which I used to use when I had Windows (extract from **/etc/fstab**):
```

/dev/hda8 /media/windows/Y vfat shortname=winnt,codepage=850,umask=000,user 0 0
```The codepage 850 should be ok for Spanish characters. See **Documentation/filesystems/vfat.txt** in the linux sourcetree for more information about the various options of the **vfat** driver.

On the other hand, if you're using **NTFS**, I'm afraid I cannot help you further.

Cheers.

---

### Post by marianom on 2006-11-21
Thanks both of you for your replies. I really appreciate it.
Will check'em with my coworkers to see if we can apply your suggestions.

---

