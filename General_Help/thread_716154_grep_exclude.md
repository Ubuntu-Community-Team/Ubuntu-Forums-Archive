---
title: "grep exclude"
date: 2008-03-05
forum: General Help
---

### Post by dbrooke on 2008-03-05
Hello!

I'm having issues with excluding directories in grep in something like this:

grep -Hin -r --exclude=admin -e 'sometexttofind' *


I am searching in directory that contains files and directories... "admin" is a directory.

Any pointers would be helpful! 

thanks,
Donovan

---

### Post by olejorgen on 2008-03-05
I think that should work, although to only exclude the one directory I think you need --exclude='^admin/.*' or somthing.
> 
--exclude=PATTERN     files that match PATTERN will be skipped.

If not I guess files like somedir/admin will be skipped too

---

### Post by dbrooke on 2008-03-05
still finds what I am trying to exclude...

but thanks for the response.

D



EDIT: I think it excludes files only... and still recursively searches all directories.  I'm trying to get it to *not* recursively search *certain* directories.

---

### Post by olejorgen on 2008-03-05
Hm.. yeah, seems like it. Sorry. Then all I can think of is xargs and find

---

### Post by dbrooke on 2008-03-05
Well that's a good start...

lets see:

find . -wholename './<yourskippeddirectory>' -prune -o -print

will skip one directory... but I don't know how set multiple directories... then to tie in
xargs!??

Donovan

---

### Post by olejorgen on 2008-03-05
Nah, then you need to -o -wholename '<second skip dir> -o <etc....> I think

-o = or

xargs are for feeding the files to grep

find <args> | xargs grep <grep args> <pattern>

Not sure if you need a second prune too

---

