---
title: "Some kind of encoding problem in my terminal"
date: 2008-03-14
forum: General Help
---

### Post by Znupi on 2008-03-14
I have some kind of encoding problem in the terminal, when opening some man pages. I'm using Ubuntu 7.10.
```

felix@felix-desktop:~$ man head
NAME[m
       head - output the first part of files

SYNOPSIS[m
       head[OPTION]... [FILE]...

DESCRIPTION[m
       Print  the  first  10  lines  of each FILE to standard output.  With more than one FILE, precede each with a header giving the file name.  With no
       FILE, or when FILE is -, read standard input.

       Mandatory arguments to long options are mandatory for short options too.

       -c --bytesé-êN
              print the first N bytes of each file; with the leading â&#128;&#152;-â&#128;&#153;, print all but the last N bytes of each file

       -n --linesé-êN
              print the first N lines instead of the first 10; with the leading â&#128;&#152;-â&#128;&#153;, print all but the last N lines of each file

       -q --quiet --silentém
              never print headers giving file names

       -v --verboseém
              always print headers giving file names

       --helpdisplay this help and exit

       --versioném
              output version information and exit

       N may have a multiplier suffix: b 512, k 1024, m 1024*1024.

AUTHORém
       Written by David MacKenzie and Jim Meyering.

REPORTINGBUGSém
       Report bugs to <bug-coreutilsàgnu.org>.

COPYRIGHTém
       Copyright Â© 2006 Free Software Foundation, Inc.
       This   is   free   software.    You   may   redistribute   copies   of   it   under   the   terms   of   the   GNU    General    Public    License
       <http://www.gnu.org/licenses/gpl.html>.  There is NO WARRANTY, to the extent permitted by law.

SEEALSOém
       The full documentation for headis maintained as a Texinfo manual.  If the infoand headprograms are properly installed at your site, the command

              infoheadém

       should give you access to the complete manual.

head 5.97                                                             September 2007                                                              HEAD(1)
pager: Symbol `ospeed' has different size in shared object, consider re-linking
ê0;felixàfelix-desktop: ûfelixàfelix-desktop:û$ clear
ê0;felixàfelix-desktop: ûfelixàfelix-desktop:û$ reset
felix@felix-desktop:~$

```
Why is this happening?

---

### Post by Znupi on 2008-03-14
Anyone? :(

---

### Post by Znupi on 2008-03-15
No one else ever experienced this? :(

---

### Post by jbird123 on 2008-03-30
If this is only happening with less, I would try to fix it by playing with your LESSCHARSET environment variable. Try either

export LESSCHARSET=latin1

or

export LESSCHARSET=utf-8

If this does not work, you may want to also try experimenting with your LC_TYPE environment variable.

export LC_CTYPE=iso_8859_1

Unfortunately, terminal encoding in Unix-land is a nightmare built on top of quicksand. These are the knobs in the system which are closest to the problem you are having.

---

