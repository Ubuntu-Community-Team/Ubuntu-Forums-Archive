---
title: "SMB and Winbind Symbols for Ubuntu 18"
date: 2023-02-13
forum: General Help
---

### Post by suaro on 2023-02-13
Hi Ubuntu Experts,

I'd like to study the SMB and Winbind source code by placing GDB breakpoints at interesting functions for running process, but unsure how to download/install proper symbols needed by GDB which match my Ubuntu build.  

Example showing I don't have proper symbols/debug modules setup:

[FONT=lucida console]< snip > 

Reading symbols from /lib/x86_64-linux-gnu/libdbus-1.so.3...(no debugging symbols found)...done.
Reading symbols from /lib/x86_64-linux-gnu/libaudit.so.1...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/samba/libheimbase-samba4.so.1...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/samba/libhx509-samba4.so.5...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/samba/libhcrypto-samba4.so.5...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/samba/libroken-samba4.so.19...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/samba/libwind-samba4.so.0...(no debugging symbols found)...done.
Reading symbols from /lib/x86_64-linux-gnu/libgpg-error.so.0...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libp11-kit.so.0...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libidn2.so.0...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libunistring.so.2...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libtasn1.so.6...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libnettle.so.6...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libhogweed.so.4...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libgmp.so.10...(no debugging symbols found)...done.
Reading symbols from /usr/lib/x86_64-linux-gnu/libheimntlm.so.0...(no debugging symbols found)...done.

              <snip > [/FONT]



The distribution of Ubuntu I'm using is :

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.6 LTS"

Any tips where I can find the matching source and debug symbols for the distribution is greatly appreciated!!

Thank you so much

---

### Post by TheFu on 2023-02-14
Standard support for 18.04 ends in a few months.  First, I'd strongly recommend moving to a newer, LTS, release.

Debug symbols are removed from production code using the 'strip' command.  Short of installing the "{package}-dev" version or recompiling from source, I don't know of a way to put symbols back into a library or program.  My knowledge could be old, but we used 'nm' and 'ar' tools to get symbols and to place .o files into libraries (.so or .a).  I know they still exist.

```

NAME
       strip - discard symbols and other data from object files
...
DESCRIPTION
       GNU strip discards all symbols from object files objfile.  The list of
       object files may include archives.  At least one object file must be
       given.

       strip modifies the files named in its argument, rather than writing
       modified copies under different names.

```


```
NAME
       nm - list symbols from object files
...
DESCRIPTION
       GNU nm lists the symbols from object files objfile....  If no object
       files are listed as arguments, nm assumes the file a.out.

       For each symbol, nm shows:
...

```

But working on Ubuntu 18 really isn't worth your time at this point.

---

### Post by suaro on 2023-02-14
I'm not limited to Ubuntu 18.  I can use any version including 22.

$ cat /etc/*lsb*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.1 LTS"


 If I use newer version,  are the steps easier ?  

 I tried building Samba project from source, but ran into all sort of missing files/binaries on both Ubuntu 18 and 22. Tried to install many missing files/dependencies, but couldn't get out of the quagmire :(  and just gave up.

Was thinking all of the needed debug files and symbols were stored someplace and it would just be a matter of copying them from some repository

---

### Post by TheFu on 2023-02-15
> **suaro said:**
> I'm not limited to Ubuntu 18.  I can use any version including 22.

$ cat /etc/*lsb*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.1 LTS"


 If I use newer version,  are the steps easier ?  

 I tried building Samba project from source, but ran into all sort of missing files/binaries on both Ubuntu 18 and 22. Tried to install many missing files/dependencies, but couldn't get out of the quagmire :(  and just gave up.

Was thinking all of the needed debug files and symbols were stored someplace and it would just be a matter of copying them from some repository

They are stored inside the object files/programs.  Look for packaged versions that end in -dev or -dbg if you want the symbols.  I don't know if they exist or not.  I don't see any for the winbind package.  There is a samba-dev in 20.04.  18.04 is too old for me. 22.04 is too new.  BTW, saying just "18" or "22" isn't sufficient, since there are 2 releases each year.

---

