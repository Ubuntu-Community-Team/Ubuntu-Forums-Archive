---
title: "dos2unix utility?"
date: 2005-05-12
forum: General Help
---

### Post by jfdill_2 on 2005-05-12
Is there a unix2dos / dos2unix utility in Ubuntu Hoary to convert between CR-LF and LF line terminations?  What package is it in?

---

### Post by fdoving on 2005-05-12
[QUOTE=jfdill_2]Is there a unix2dos / dos2unix utility in Ubuntu Hoary to convert between CR-LF and LF line terminations?  What package is it in?[/QUOTE]
 Yes there is.
It's in the package named 'sysutils'.
The commands are 'todos' and 'fromdos'


- Frode

---

### Post by pschulz01 on 2005-06-10
[QUOTE=jfdill_2]Is there a unix2dos / dos2unix utility in Ubuntu Hoary to convert between CR-LF and LF line terminations?  What package is it in?[/QUOTE]

Package: flip

To convert to*NIX format..
> flip -u <filename>

See 'man flip' for more information

---

### Post by charlieg on 2005-08-10
Ah perfect.  I wonder if the actual 'dos2unix' app is available in Debian/Ubuntu though.  Still, since flip does the job, don't think I'll investigate further.

---

