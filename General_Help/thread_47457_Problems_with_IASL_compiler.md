---
title: "Problems with IASL compiler"
date: 2005-07-08
forum: General Help
---

### Post by djpenguin on 2005-07-08
I'm setting up ubuntu on a laptop for a friend, an ASUS Z71A.  As is typical with laptops under linux, the DSDT (Differentiated System Description Table) is not working right.  This is the file that tells ACPI what devices exist and how the are organized heirarchically.  I know the DSDT is bad from aprevious attempt to run gentoo on the laptop, but in order to fix it, I need to compile the [Intel ASL compiler](http://developer.intel.com/technology/iapc/acpi/downloads.htm) to work with the DSDT.

This is where I run into problems.  After doing the configuration steps, i run the 'make' command and get the following output:

```
root@carl:/sbin/acpica-unix-20050624/compiler # make
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include  
  -c -o aslcompilerlex.o aslcompilerlex.c
aslcompiler.l: In function `comment':
aslcompiler.l:847: error: `yytext_ptr' undeclared (first use in this function)
aslcompiler.l:847: error: (Each undeclared identifier is reported only once
aslcompiler.l:847: error: for each function it appears in.)
make: *** [aslcompilerlex.o] Error 1

```

I have to admit that I am stumped by this.  Any ideas on how to get this tool to compile?

---

### Post by jewishj on 2005-08-23
I had the same problem today and I was able to fix it by reverting to flex-old and bison (from flex and bison++).  I then had to delete the extracted folder with iasl and re-extract it and start over for it to work.

---

### Post by avilella on 2006-03-21
another thing that seems to work is to comment the line:

#undef yytext_ptr
to
/*#undef yytext_ptr*/

in compiler/aslcompilerlex.c

---

