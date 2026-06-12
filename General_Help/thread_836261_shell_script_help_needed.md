---
title: "shell script help needed"
date: 2008-06-21
forum: General Help
---

### Post by dexter.deepak on 2008-06-21
i have the list of all installed packages of the form :
a              install
b              install
c              deinstall
d              install

now i want to issue an install command for "all" the "installed" packages.
so i think of a script which makes the above list as:
a b d
...so that i can append the entry after "sudo apt-get install".

i just cant think any solution to this :confused::confused::confused:

---

### Post by nick_h on 2008-06-21
Try something like:
```
grep ' install' list.txt | cut -d ' ' -f 1
```

---

### Post by dexter.deepak on 2008-06-21
thanks a lot !!
i havent read shell-scripting to this extent till now but this is reallly interesting :cool:

the script is fine for the example i gave you, but it aint solving my purpose..the reason(probably) being that , the list is of the form:
a<tab><tab><tab>install
and not of the form :
a<space><space>install

when i try to replace the 'space' in the string you gave me with 'tab' or 'multiple spaces', i fail.
so what next ??

---

### Post by dexter.deepak on 2008-06-21
i know, i am going to ask you too much over this platform...but can you please explain a bit further the command you gave me ??
thank you.

---

### Post by nick_h on 2008-06-21
Try:
```
grep '\Winstall' list.txt | cut -f 1
```

*grep* searches for patterns within files.  \W matches whitspace.  The whole line will be returned.

The pipe symbol | passes the output of one command to the input of the next.

*cut* returns a specified section of a line. -f 1 returns the first field.  -d ' ' sets the field delimeter to a space (the default is a tab).

---

### Post by lloyd_b on 2008-06-21
> **dexter.deepak said:**
> thanks a lot !!
i havent read shell-scripting to this extent till now but this is reallly interesting :cool:

the script is fine for the example i gave you, but it aint solving my purpose..the reason(probably) being that , the list is of the form:
a<tab><tab><tab>install
and not of the form :
a<space><space>install

when i try to replace the 'space' in the string you gave me with 'tab' or 'multiple spaces', i fail.
so what next ??

The "cut" command will automatically use <TAB> as a delimiter, if no "-d" option is specified, so
```
grep 'install' list.txt | cut -f 1
```
should work, provided that those are *always* <TAB>s, and not <SPACE>es.  If you've got a mix of tabs and spaces, I'd suggest passing it through "tr" to translate the spaces to tabs first:
```
grep "install" list.txt| tr ' ' '\t' | cut -f 1
```
(in case it's not obvious to you, "tr" translates all occurrences of the first character (" ") to the second character ("\t", which represents <TAB>).

Hope this helps...

---

### Post by pietjanjaap on 2008-06-22
command 1; command 2

    Runs 1 then 2

command 1 && command 2

    runs 1, 2 only if 1 completes without error

command 1 || command 2

    runs 2 only if 1 fails

command 1 \
command 2

    use \ to continue commands on multiple lines





Sorry for the confusion

\ = continue on a new line

you need

command 1 ;\
command 2

You can break it up :

com\
and 1\
;\
command 2

any how you want, the point is to take :

command 1; command 2; command 3

and make it easier to read

command 1;\
command 2;\
command 3

(Hit the <enter> key after the \ and after the last command to execute all 3)

As far as running several commands at the same time, depends on the command, try starting them in a sub shell if needed:

Code:

command 1 &; command 2

Subshell = (command 1)

Code:

(command 1&); command 2

---

### Post by dexter.deepak on 2008-06-22
thanks a lot to all of you !!:guitar:
it was a great learning experience for me . i finally tried :
 grep '\Winstall' ~/Desktop/installed-pkgs | cut -f 1 | tr '\n' ' ' > list2

this aligned the output horizonatlly, i.e from :
a
b
to :  a b
 i could have tried pietjanjaap's method of adding a line break \, but that would have proved lengthy.

just few more queries:
1. how do we define a delimiter ? what is it ?
2. how to pass this new "file" as an argument to apt-get install ?

---

### Post by nick_h on 2008-06-22
I think you are trying to get to something like:
```
#!/bin/bash
PKGS=`grep '\Winstall' ~/Desktop/installed-pkgs | cut -f 1`
CMD='sudo apt-get install '$PKGS
`$CMD`
```

However, this functionality already exists in the *dpkg* command.  From the *dpkg* manual page:
> To make a local copy of the package selection states:


     dpkg --get-selections >myselections


You might transfer this file to another computer, and install it there
with:


     dpkg --clear-selections
     dpkg --set-selections <myselections


Note that this will not actually install or remove anything, but just
set the selection state on the requested packages. You will need some
other application to actually download and install the requested
packages. For example, run dselect and choose Install.


---

### Post by dexter.deepak on 2008-06-22
thanks once more.
this was what i was trying to do as i had got the getselections list,but i didnt know about setselections too !!

---

