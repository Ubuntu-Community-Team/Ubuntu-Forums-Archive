---
title: "unzipping tar.gz files"
date: 2007-07-26
forum: General Help
---

### Post by prem1er on 2007-07-26
How do I unzip tar.gz files in the terminal.  I downloaded a file that is just source code and it came in a directory with a tar.gz extension.  How do I do this.  Thanks.

---

### Post by DoktorSeven on 2007-07-26
Open with file-roller, ark, or from a commandline with
**tar zxfv *filename*.tar.gz**

---

### Post by nyinge on 2007-07-26
```
 tar -xzf filename.tar.gz 
``` will extract files into a folder, usually with that filename.

---

### Post by meho_r on 2007-07-28
And what about multiple files? Is there a way to extract multiple .tar files with one command?

---

### Post by p_quarles on 2007-07-28
> **meho_r said:**
> And what about multiple files? Is there a way to extract multiple .tar files with one command?
There are a couple ways to do that. One is to use piping by placing the "|" character between individual commands:
```
tar -xzf filename1.tar.gz | tar -xzf filename2.tar.gz
```
That way, you can enter one (longish) line of commands, and then leave while it performs those operations in succession.

The other way is (I haven't done this, but it should work) to use variables. For instance the "*" character will find any string of any length in the place where you put it. There are many other variables, but I use this as a simple example. If you typed:
```
tar -xzf *.tar.gz
```
It would unpack and decompress every file in your current folder that ended in "tar.gz".

---

### Post by dagnabit dang doohickey on 2007-07-28
> One is to use piping by placing the "|" character between individual commands
What would be the point of piping multiple tar commands together? Wouldn't separating the tar commands with semicolons or ampersands be more appropriate?
```
tar xzvf filename1.tar.gz ; tar xzvf filename2.tar.gz
```


> Is there a way to extract multiple .tar files with one command?
To batch extract a directory full of tar.gz files, you can use this:
```
cat *tar.gz | tar xzvi
```

---

### Post by meho_r on 2007-07-28
> **dagnabit dang doohickey said:**
> 
To batch extract a directory full of tar.gz files, you can use this:
```
cat *tar.gz | tar xzvi
```

Yeah, that's it! It seems that option ''-i'' is the key point. Thanks guys :D

---

### Post by shahjapan on 2008-02-20
Thanks to all

It works fine :)

---

