---
title: "need to move a folder"
date: 2015-02-28
forum: General Help
---

### Post by Autodave on 2015-02-28
I downloaded the help file for Audacity.  It is in a folder on my desktop and I need to move it into the audacity folder.  Can someone give me the command I need to move or copy it?

---

### Post by ian-weisser on 2015-02-28
One way:
```
mv /where/it/is/filename /where/you/want/it/filename
```

WARNING: mv doesn't have an 'undo'.
Note that mv can also be used to simply rename a file.

mv has many options. See man mv for the complete list.

---

### Post by Autodave on 2015-02-28
Itried to copy it with this command:
~$ cp /home/dave/Desktop/help/ /usr/share/audacity/

And I get this: cp: omitting directory &#8216;/home/dave/Desktop/help/&#8217;


It did not copy it and I cannot figure out why.  Any idea what I am doing wrong?

---

### Post by Autodave on 2015-02-28
The folder I am trying to move or copy is on my desktop and named "help". I want to move or copy it to the audacity folder which is in usr/share/audacity .  What command do I need?

---

### Post by ian-weisser on 2015-02-28
You have the command you need.
You just are not using it properly. Look at the manpage.

Hint: Try it with the -r flag. You want to move the folder *with all contents*.

---

### Post by ajgreeny on 2015-02-28
Here's how to do it, assuming all the directions given in the thread are the same as you have done so far.
[http://askubuntu.com/questions/258272/how-to-install-audacitys-manual](http://askubuntu.com/questions/258272/how-to-install-audacitys-manual)

---

