---
title: "cpio - Nasty Surprise"
date: 2005-07-19
forum: General Help
---

### Post by cosmolee on 2005-07-19
I'm trying to back up directories with `cpio`.  The file generated is  about 10GB large.  When I try to read the file back in, I get the error message:

     cpio: standard input is closed: Value too large for defined data type

Any I idea what this is about?  I've tried various options, -H newc, -H crc, & no option, but I can't read back the file that I wrote out!


Sample:

# cpio -o -H newc < bup.lst > cosmo.cpio

# cpio -ivt < cosmo.cpio
cpio: standard input is closed: Value too large for defined data type
#
 
BTW, this doesn't appear to be specific to Ubuntu or Debian.  I got the same problem with Fedora and some other Debian distros....

It's a good thing I tried to read the file before I blew away my disk partition!

Cosmo   ](*,)

---

### Post by cosmolee on 2005-07-19
Well, I didn't find an explanation, but I found a solution:

$ cat cpio-file | cpio -i


In other words, pipe the cpio file to `cpio` with `cat`.

HTH.

---

