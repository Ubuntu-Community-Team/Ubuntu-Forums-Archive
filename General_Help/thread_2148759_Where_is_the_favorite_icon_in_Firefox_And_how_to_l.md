---
title: "Where is the favorite icon in Firefox? And how to list full file attributes"
date: 2013-05-26
forum: General Help
---

### Post by ruwan2 on 2013-05-26
Hi,
I just install Ubuntu on a computer, but I cannot find the favorite icon after I have saved several web site in it (and I have created a folder for it). That is, my question is about firefox settings. Thanks,

The second question is about the shell. What is the default shell name?
When I enter "sh" in the shell, it changes pre-words in the shell to a '$" sign. What is the status?


My third question is about how to list files in a folder with detailed attributes? It is different with 'l' and 'ls' in OPENSUSE. I find that there is no difference in Ubunto.


Thanks again.

---

### Post by Cheesemill on 2013-05-27
> **ruwan2 said:**
> My third question is about how to list files in a folder with detailed attributes? It is different with 'l' and 'ls' in OPENSUSE. I find that there is no difference in Ubunto.

I don't know how Suse does things but the ls command used in Ubuntu is the standard Linux ls command. Maybe you are thinking of...
```
ls -l
```

For more details look at the man page for ls....
```
man ls
```

---

### Post by efflandt on 2013-05-27
I am not even sure where firefox caches data, since I cannot find that under ~/.mozilla/firefox

If you save a web page maybe it does not save the favicon.png file for the site.

The default login shell is **bash**, but if you type **sh** (or use #!/bin/sh for the shebang line of a script) you end up in **dash** shell which is smaller and quicker, but missing some of the extensive things that bash can do.  For the differences read **man bash** and **man dash** in a terminal.

---

### Post by peter d on 2013-05-27
> **ruwan2 said:**
> Hi,
I just install Ubuntu on a computer, but I cannot find the favorite icon after I have saved several web site in it (and I have created a folder for it). That is, my question is about firefox settings. Thanks,

The second question is about the shell. What is the default shell name?


If you mean the bookmarks icon, go to View>Toolbars>Customise and drag the Bookmarks icon where you want it.

---

### Post by deadflowr on 2013-05-27
```
lsattr
```
list file/folder attributes
```
man lsattr
```
To learn what those attributes could be.

---

