---
title: "Images downloaded off the net where executable!"
date: 2007-07-01
forum: General Help
---

### Post by arsenic23 on 2007-07-01
Here's something odd that I noticed today:
I sat down this morning to write a quick script that would change all my randomly named images in my dump folders to nice four didget numerical names.  I got the script working, ran it in my first image dump folder, and then moved on to number two.  The first thing I did was ls to take a look at the contents before I killed them and...  some of those images showed up as yellow(executable).  I double checked and they were executable!  

A quick `chomod a-x *` and I was feeling better but, shouldn't that only be possible if I make them executable  myself?  All those images where downloaded from Opera using right-click>save, so I'm just a little puzzled on that.

---

### Post by cookies on 2007-07-01
Weird....

But, yes, anything you download from the net can be set as executable by someone, but images shouldn't be.....

---

### Post by arsenic23 on 2007-07-01
Really?  Huh, I was under the impression that everything I saved from a browser would/should be -rw-r--r--.  Good to know.

---

### Post by cookies on 2007-07-01
As an example: if you download a Bash script, and the person who made it set it as executable, it will be for you, too. 

I still don't get why someone made images executable....

---

