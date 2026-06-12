---
title: "Move and keep two files of the same name"
date: 2015-08-29
forum: General Help
---

### Post by simon114 on 2015-08-29
Hi community,
I have just made the leap to Ubuntu 14, quite painlessly I might add.Thank you for what appears to be an amazing OS.

My question is this.
I regularly update a zip folder and before I over-write the info into the zip, I save it along with all the other copies of the previous zips.
so in a folder i have 
file.zip
file01.zip
file02.zip   ....etc
Windows 7 has an option to auto rename the two identically names files in the same folder.
How can i do this in Ubuntu 14. As when I try to move the zip file it only gives me the option to replace the existing zip file with the new one, and keeping them all is essential for backup reasons.

Thank you very much for your help, I hope I have explained myself on what is my first post.

---

### Post by HermanAB on 2015-08-29
Make a subdirectory.

---

### Post by simon114 on 2015-08-29
Hi Herman, yeah I had figured I could make hundreds of sub directories, so I'm guessing its not possible.

---

### Post by vasa1 on 2015-08-29
What about *man mv*? One option is *--backup=numbered*
```
       --backup[=CONTROL]
              make a backup of each existing destination file

```
Would that be of any help?

---

### Post by simon114 on 2015-08-29
Hi vasa,
 I am new to Ubuntu so i wouldn&#8217;t know how to implement this, some more information would be great, thanks.

---

### Post by Dennis N on 2015-08-29
Use copy (cp) command with it's backup option set to 'numbered'. (The move (mv) command has the same --backup option. So the example below should work with mv as well.)

Example: Initially, b-directory and f-directory both had one copy of a-file and d-file. After two successive backups of b-directory to f-directory: 

```
dmn@Sydney:~/work/testing$ cp --backup=numbered b-directory/*-file f-directory/
dmn@Sydney:~/work/testing$ tree
.
&#9500;&#9472;&#9472; b-directory
&#9474;   &#9500;&#9472;&#9472; a-file
&#9474;   &#9492;&#9472;&#9472; d-file
&#9492;&#9472;&#9472; f-directory
    &#9500;&#9472;&#9472; a-file
    &#9500;&#9472;&#9472; a-file.~1~
    &#9500;&#9472;&#9472; a-file.~2~
    &#9500;&#9472;&#9472; d-file
    &#9500;&#9472;&#9472; d-file.~1~
    &#9492;&#9472;&#9472; d-file.~2~


```

---

### Post by vasa1 on 2015-08-31
> **Dennis N said:**
> Use copy (cp) command with it's backup option set to 'numbered'. (The move (mv) command has the same --backup option. So the example below should work with mv as well.)
...
Nice!

*cp* has this as well:
```
       -u, --update
              copy  only  when the SOURCE file is newer than the destination file
              or when the destination file is missing
```
And *mv* has the equivalent as well.

---

