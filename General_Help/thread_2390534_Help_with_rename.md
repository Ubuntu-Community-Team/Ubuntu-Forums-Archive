---
title: "Help with rename"
date: 2018-04-29
forum: General Help
---

### Post by mathieud on 2018-04-29
I have never been lucky with `rename` but today I get stuck with a real problem:
```

/tmp/test_rename$ touch foo.bak bar.bak
/tmp/test_rename$ rename 's/\e.bak$//' *.bak
/tmp/test_rename$ ls
bar.bak  foo.bak

```
In other words, the example that is given in `rename(1p)` man page doesn't work (I use the `perl` version but I got similar issues under another distribution which use the `util-linux` version).

Am I missing something ?

---

### Post by yetimon_64 on 2018-04-29
The rename command you are running above is not the same as the example in the man file.
You have included an extra "e" in your command before the ".bak".
Try running the next code box, as taken from the man file, with your examples "foo.bak" and "bar.bak" again ...
```
rename 's/\.bak$//' *.bak
```

From my install the rename man  file example works (no extra "e" included ;-) ) ...
```
yetiman:~/Desktop $ touch foo.bak bar.bak
yetiman:~/Desktop $ ls
bar.bak  foo.bak
yetiman:~/Desktop $ rename 's/\.bak$//' *.bak
yetiman:~/Desktop $ ls
bar  foo
yetiman:~/Desktop $
```

Basically you are having trouble with a typing error here.

Regards, yeti.

---

### Post by mathieud on 2018-04-30
Your example works but the \e is included in the man page (see attachment). I'm using Ubuntu 16.04 for now but I have seen the same problem under fedora 27.

---

### Post by steeldriver on 2018-04-30
Hmm... yes that does seem to be an error in the troff source for the manpage

---

### Post by yetimon_64 on 2018-04-30
> **mathieud said:**
> Your example works but the \e is included in the man page (see attachment). I'm using Ubuntu 16.04 for now but I have seen the same problem under fedora 27.
Ah, ok, there is an error in the man page of the version you are using then, not a typo on your part. I am checking this on 14.04 btw so maybe an error has crept into the newer version you are now using.

Apart from a simple error I can't see any point of that command using a backslash to escape the letter "e", whereas a period (.) does need such used. Maybe this needs a bug report lodged to get the problem you have come across with rename fixed. I was a bit surprised on seeing your attachment but such errors do pop up from time to time.

Regards, yeti.

---

### Post by mathieud on 2018-04-30
Thanks to both of you for confirming that I'm not 100% crazy. I will try to report it where appropriate.

---

### Post by mathieud on 2018-05-02
The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/libfile-rename-perl/+bug/1768150](https://bugs.launchpad.net/ubuntu/+source/libfile-rename-perl/+bug/1768150). I will close the question according to the status of the bug.

---

### Post by yetimon_64 on 2018-05-02
> **mathieud said:**
> The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/libfile-rename-perl/+bug/1768150](https://bugs.launchpad.net/ubuntu/+source/libfile-rename-perl/+bug/1768150). I will close the question according to the status of the bug.

I just noted the package name you are using "libfile-rename-perl" in the bug report and checked my 14.04 install; I was commenting on the standard version apparently as libfile-rename-perl was not installed here. I installed the libfile-rename-perl version in 14.04 and rather interestingly the bug is now showing here as well, see next code box ... ```
RENAME(1p)                                   User Contributed Perl Documentation                                  RENAME(1p)

NAME
       rename - renames multiple files

SYNOPSIS
       rename [ -h|-m|-V ] [ -v ] [ -n ] [ -f ] [ -e|-E perlexpr]*|perlexpr [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified as the first argument.  The perlexpr argument
       is a Perl expression which is expected to modify the $_ string in Perl for at least some of the filenames specified.
       If a given filename is not modified by the expression, it will not be renamed.  If no filenames are given on the
       command line, filenames will be read via standard input.

       For example, to rename all files matching "*.bak" to strip the extension, you might say

               **rename 's/\e.bak$//' *.bak**

```I have bolded the example in 14.04 libfile-rename-perl version which also shows the bug.

Sorry for the misinformation/misunderstanding, you may need to correct the bug report as the bug does exist in 14.04 in that particular libfile-rename-perl file as well. Apparently my previous comments were mistakenly referring to the standard rename file that comes installed in ubuntu 14.04 not the libfile-rename-perl version.

**Edit:** I just purged libfile-rename-perl and now have /usr/bin/prename supplying the only alternative for /usr/bin/rename and have gone back to the same as before; the man file example has no "e" in it (which works fine as before). Some of my confusion came about in that the standard rename option has > Perl Programmers Reference Guide at the top of the man file as compared to libfile-rename-perl showing... > User Contributed Perl Documentation Both indicate perl but are from different sources apparently.

Regards, yeti.

---

