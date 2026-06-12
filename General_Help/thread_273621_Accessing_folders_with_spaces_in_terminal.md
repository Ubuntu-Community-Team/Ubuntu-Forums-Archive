---
title: "Accessing folders with spaces in terminal"
date: 2006-10-08
forum: General Help
---

### Post by Old Pink on 2006-10-08
Say I wanted to access:
> /home/matt/spaced out folder name/folder/
in terminal, how do I go about doing it?

Usually I'd type:
> cd /home/matt/spaced out folder name/folder/
But I just get: > matt@matt-desktop:~$ cd /home/matt/spaced out folder name/folder/
bash: cd: /home/matt/spaced: No such file or directory
matt@matt-desktop:~$
It stops before the first space. :-k

It may just be my immagination, but I think this has only just started happening... ](*,)

---

### Post by meng on 2006-10-08
Escape characters:
backslash before each space
cd /home/matt/spaced\ out\ fold...(etc)

Even better, type a few characters and press TAB for autocompletion.

---

### Post by Old Pink on 2006-10-08
Thanks. :) 

So I just noticed it? Or has it just started? I've been a Ubuntu user for over a month now, seems strange if I'd only just noticed it.

---

### Post by DarthMandeep on 2006-10-08
I usually type the first part of the directory name and then hit tab to auto-complete. You can also place a "\" before each space if you really want to type out the whole directory name.

Edit: Got beaten to the punch. Oh well. ;)

---

### Post by Cronjob on 2006-10-09
If it's just a filename or the last directory at the end of a path, you can simply put quotes around it.

ie:

cd /music/"the matches"

---

