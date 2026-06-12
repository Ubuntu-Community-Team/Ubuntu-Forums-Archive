---
title: "Alias help: How do I represent filenames/directories?"
date: 2008-01-22
forum: General Help
---

### Post by TobyReynolds on 2008-01-22
If possible, I would like to create a couple of aliases for commands where a filename/directory (different each time) is placed in the middle. How do I do it please?

More specifically, this is what I want to do:

1. Compile FORTRAN 90 code with gfortran and make the output filename (specified by '-o') the same as the input name (but without the .f90 extension, or with extension .exe).
So something like:
```
alias f90=' gfortran -o SAME_FILENAME -O2 -g SAME_FILENAME.f90 '
```
or
```
alias f90=' gfortran -o SAME_FILENAME.exe -O2 -g SAME_FILENAME.f90 '
```
Is there something I can replace SAME_FILENAME with to achieve this? If possible, I don't want to have to type the .f90 part.

2.Change permissions of files and directories, under a specified directory, separately using the following code ([as described here]("https://help.ubuntu.com/community/FilePermissions")):
```
sudo find /path/to/someDirectory -type f | while read var1; do sudo chmod 644 "$var1"; done
sudo find /path/to/someDirectory -type d | while read var1; do sudo chmod 755 "$var1"; done

```What do I replace /path/to/someDirectory with in an alias?

Thanks for any help.
Toby

---

### Post by dagnabit dang doohickey on 2008-01-22
While its not possible to do what you're asking with an alias, you can do it with a function.
Example:
```
function f90 () { gfortran -o "$*.exe" -O2 -g "$*.f90" ; }
```
The functions can then be added to your .bash_aliases file, just as you would an alias.

---

### Post by TobyReynolds on 2008-01-22
Thanks for your reply dagnabit.
Can $* also be used in the second instance to represent where a directory will be entered, or do I need something different here? (I'm reluctant just to test it myself as I don't want to mess around with changing permissions.)
Also can you tell me what the quotation marks (") are for (and why they encompass the filename extension too) and also the semi-colon (; ) at the end please? I'd like to understand the code so I can maybe write more complicated functions later.

---

