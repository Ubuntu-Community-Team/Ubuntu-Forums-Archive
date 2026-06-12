---
title: "srm command questions"
date: 2008-05-31
forum: General Help
---

### Post by prophet665 on 2008-05-31
I was looking around the net for an Ubuntu/Linux equivalent of the Eraser program on Windows.  I found out about the srm command, but I have a few questions:

1.  How many times is it overwriting the target file/files?
2.  Is it using pseudo-random data or successive paths of ones and zeroes?
3.  Is there another command that is better for what i am looking to do?

---

### Post by prophet665 on 2008-05-31
Maybe this should be moved to the security forum?

---

### Post by pointone on 2008-05-31
```
man srm
```

```
       -m, --medium
              overwrite the file with 7 US DoD compliant passes  (0xF6,  0x00,
              0xFF, random, 0x00, 0xFF, random)
```

```
       The -s option overrides the -m option, if both are present.  If neither
       is specified, the 35-pass Gutmann algorithm is used.
```

---

### Post by prophet665 on 2008-05-31
Damn..I could swear I checked the man page earlier and it didn't have that info.  Thanks for pointing me to it (again!).

---

### Post by prophet665 on 2008-05-31
I was reading other forums posts and one of the things that was brought up was a journaling file system like ext3 cannot be securely deleted using srm.  

After reading many, many other posts I am coming to the conclusion that a combination of today's large hard drives, cheaper equipment, and journaling file systems, it is almost impossible to securely erase your data.

I know TrueCrypt has whole drive encryption for a Windows machine and one of the action items is to create whole drive encryption for Linux.  Does anyone do this currently?

---

