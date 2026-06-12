---
title: "recursively remove brackets from directory names"
date: 2015-10-19
forum: General Help
---

### Post by sohlinux on 2015-10-19
Hello, how can I recursively remove brackets from directory names? 

eg. all directories called (fred) will be named fred

or remove any character or string of characters from directory name recursively

eg. tommy will be then named tom

thanks

---

### Post by TheFu on 2015-10-19
I would write a **find** command.
A few similar examples:
* [https://stackoverflow.com/questions/15007058/find-files-rename-in-place-unix-bash](https://stackoverflow.com/questions/15007058/find-files-rename-in-place-unix-bash)
* [https://unix.stackexchange.com/questions/172186/find-xargs-and-mv-renaming-files-with-double-quotes-expansion-and-bash-preced](https://unix.stackexchange.com/questions/172186/find-xargs-and-mv-renaming-files-with-double-quotes-expansion-and-bash-preced)
* [https://unix.stackexchange.com/questions/38454/how-to-remove-the-1-from-filenames-using-the-find-command](https://unix.stackexchange.com/questions/38454/how-to-remove-the-1-from-filenames-using-the-find-command)

---

### Post by Lars Noodén on 2015-10-19
+1 for 'find'.   I would also use that for the recursive part.  

However, for renaming based on patterns, I would use the program 'rename'.  It can be combined with 'find' to recursively rename files.

---

### Post by sohlinux on 2015-10-19
I have been googling , reading, trying and testing for hours with no luck. does anyone know of a simple one liner to do this? thanks

---

### Post by TheFu on 2015-10-19
Please post what you've already tried. Teaching you to fish in my intent ... not handing you a fish for lunch. 

BTW, is it a non-trivial thing and it usually takes me 5-10 attempts to get it working too. ;)

---

### Post by sohlinux on 2015-10-19
I like to learn to fish but after a few hours of trying it can become daunting
for example the following is supposed to work but does nothing
it is supposed to change the bracket for a dash

find /home/test -type f -execdir rename 's/(/-/' '{}' \;

---

### Post by Lars Noodén on 2015-10-19
You are probably trying to get something like this:

```

 find . -type f -execdir rename -n '[color=blue]s/\(/-/g;[/color] [color=purple]s/\)/-/g;[/color]' '{}' \;

```

The parentheses need to be escaped, thus the backslash. And there are two s/// replacements, one for each parenthesis.  The -n tells it not to do anything, just test the expression, take it out when you have the results you want.

'rename' can handle any perl expression.

---

### Post by TheFu on 2015-10-19
> **sohlinux said:**
> 
find /home/test -type f -execdir rename 's/(/-/' '{}' \;


Close. Parenthesis must be escaped inside regex.  Also, I thought you wanted to rename directories, not files? the "-type f" only returns files. Use "-type d" for directories. I've never used execdir... don't know how that works, but ...

```
find /home/test -type d -execdir rename 's/\(/-/' {} \;
```
should handle the left parens. I did get an error, but it worked. My attempt without using execdir failed here. ;|

---

### Post by sohlinux on 2015-10-19
thanks for your help guys but it will not work for me , it shows no error and does nothing even with -n removed so I will probably have to rename the directories manually. I spent the best part of the day trying. I used to use a gui for this sort of thing, krename I think,  it was great but this particular install of ubuntu im accessing remotely doesnt have the desktop so I cant use guis thats why I have been trying to do it from the command line. it was fun trying :)

---

### Post by TheFu on 2015-10-19
I tested the script and it worked on a 14.04 server. -n would have to be removed.  Did you fix the "type" issue?

---

### Post by sohlinux on 2015-10-19
yes I changed to type d. maybe something is missing on this server. ill try again locally and see if it works.

---

### Post by TheFu on 2015-10-19
**rename** may not exist.  find is a core part of binutils. Can't imagine any Unix-OS working without it.

Post the exact command back.  Perhaps something unexpected crept in?

---

