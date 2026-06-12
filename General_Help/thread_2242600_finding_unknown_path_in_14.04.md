---
title: "finding unknown path in 14.04"
date: 2014-09-02
forum: General Help
---

### Post by harlie on 2014-09-02
Hello; I need to find the path to a file I know the name of but not the location. I have been searching all of the folders in the   "places" under  "computer" and not finding the file I want to find and remove. I can't find a command line tool to do this.
But I am sure a command exists to find lost files, just what is it.
thanks 
harlie

---

### Post by westie457 on 2014-09-02
would the 'locate' command help you? for details ```
man locate
```

---

### Post by Dennis N on 2014-09-02
A general way is to use the **find** command in the terminal.

Find files (somewhere in my home folder) containing "city" as part the filename:

```
dmn@Erica:~$ find -iname *city*
./work/Audacity
./images/Inkscape/import/unknown1-sac-city-iowa-mirror.png
./images/Inkscape/import/unknown1-sac-city-iowa.png
./.audacity-data
./.audacity-data/audacity.cfg

```
[more output omitted]

---

### Post by harlie on 2014-09-02
thanks I will try both.

---

### Post by nerdtron on 2014-09-02
If you don't know the location, you should search from the root directory, and try to search using sudo so that you can view all files.

```
sudo find / -iname *file*
```

---

### Post by Vaphell on 2014-09-02
minor correction related to find examples posted here.
pattern provided with -name needs to be quoted or escaped to prevent accidental errors.

in case there are files matching the unquoted glob in the current dir, in the very first step the shell will expand the glob to the list of files, which throws the find's logic off.

Let's consider 2 cases
1. in the current directory there is a file called test1.txt
running
```
find -name *test*
```
will turn into
```
find -name test1.txt
```
even before find gets to run. As a result find looks for a fixed name, not a pattern which is not the desired action.

2. in the current dir there are multiple files matching the glob, eg test1.txt, test2.txt, test3.txt
again, glob gets expanded to proper names
```
find -name test1.txt test2.txt test3.txt
```
but this time the command doesn't even make sense due to unexpected arguments. first filename is attached to -name as a fixed string but the rest is just dangling there, not making any sense from the find's point of view.


If you want to pass the glob to find untouched, you need to hide it from shell, either by quoting '*test*' or escaping \*test\*

---

