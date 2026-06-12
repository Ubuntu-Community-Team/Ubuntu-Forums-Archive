---
title: "Use find command to look for specific text in asci files?"
date: 2006-12-25
forum: General Help
---

### Post by TuxCrafter on 2006-12-25
Use find command to look for specific text in asci files?

Hello, I know the find command is a very powerful command with a lot of options.

I have read this page for more info on the find command:
[http://www.codecoffee.com/tipsforlinux/articles/21.html](http://www.codecoffee.com/tipsforlinux/articles/21.html)
I also know that “man find” excists.

The background behind my guest ion. 

I am using Linux xubuntu 6.10 kernel 2.6.19.1. And I wanted to install vwmare server. I have a script for that that usually works great. However this time it was giving me annoying errors when compiling the modules (net).

It appears my new kernel and the vmware source where not compatible. It was looking for CHECKSUM_HW declarations that where not there. So I had do a long trial and error and changed a few files in the vmware module source to get it working again with success. (I attached the vmware source code for the module)

What I needed was a command to search for “CHECKSUM_HW” in all the source files of a given directory and returned the files and lines that match.

OR

I want a command that looks for “searchstring” in directory “/” in all “text files” and return me these files with the matching lines.

So how do I do this?

---

### Post by Vox754 on 2006-12-25
I think your post scares most beginners.
There is also a forum dedicated to programming, may be you'll find help there.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by TuxCrafter on 2006-12-25
> **Vox754 said:**
> I think your post scares most beginners.
There is also a forum dedicated to programming, may be you'll find help there.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

I did not intend to scare someone. I thought it was a general question because the find tool is a general tool available in all linux distributions. Does someone now how to replace this topic to the programming section. Nice tip btw I did not know it existed.

---

### Post by darenw on 2006-12-25
perhaps you want grep ?

---

### Post by TuxCrafter on 2006-12-25
> **darenw said:**
> perhaps you want grep ?

It should become a combination with find and grep but I don't now how to use it. It sould be possible with the exec function of find but I don't know how yet.

---

### Post by majoridiot on 2006-12-25
the following command will search all files in the current directory for the search string and
output the relevant line number and file:

```
grep -n -o <searchstring> *
```

in your case, it would be:

```
grep -n -o CHECKSUM_HW *
```

or, if there are more files than you care to scroll through:

```
grep -n -o CHECKSUM_HW * > ~/Desktop/found.txt
```
 
will output the file list and line numbers to found.txt on your desktop.
grep is unbelievably powerful... check out the man page.

```
man grep
```

---

### Post by TuxCrafter on 2006-12-26
Did some more research on the idea's you gave me and come up with the following working command:

```
 sudo find / -name '*.c' -exec sudo grep -H -n "CHECKSUM" '{}' \
```

Works brilliant will be a time saver. (power to linux)

Thanks everyone I found the answer

---

