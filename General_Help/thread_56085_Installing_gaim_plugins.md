---
title: "Installing gaim plugins?"
date: 2005-08-11
forum: General Help
---

### Post by Grey Breaker on 2005-08-11
Alright, I've got the perl file and such, and the instructions say to fing the .gaim folder and make a folder called 'plugins' if it doesn't exist, and also put the help file in another folder. 

So I enabled the ability to view hidden folders and ran a search. Found two folders called 'Gaim', neither hidden and I'm not allowed to create folders in either of them. 

I'm stuck. Am I gonna have to do this from the root command and if so, which gaim folder do I send this stuff to?

---

### Post by heimo on 2005-08-11
That .gaim most probably refers to directory in your home directory. It's usual place for user specific configuration / plugins.
 ```
~/.gaim
is equal to
/home/[your_username]/.gaim

```

---

### Post by Grey Breaker on 2005-08-11
Alright, found it and followed the instructions. Rebooted gaim and... it doesn't find anything new. Nothing new under the plugins list.

Any ideas?

---

### Post by heimo on 2005-08-11
Which instructions are you following? And where did you get those plugins? I can see that in directory /usr/lib/gaim seems to be stuff that looks like plugins in Gaim. If you know the source of those plugins (trust that they are not harmful) you can try to copy them into that directory using 
 ```
sudo cp [source] [destination]
```
where source is the file to copy, destination is directory /usr/lib/gaim

---

### Post by Grey Breaker on 2005-08-11
Tried that, no success.

The plugin I wish to install is at [http://sourceforge.net/tracker/index.php?func=detail&aid=1216735&group_id=235&atid=390395](http://sourceforge.net/tracker/index.php?func=detail&aid=1216735&group_id=235&atid=390395)

Could someone have a look and see if theirs something wrong with it, or would I have to install some sort of perl client? I'm following the instructions to the letter, and I've been playing with Ubuntu for less then a week... so I don't know anything. Is their something obvious to you guys that isn't included in the instructions?

---

### Post by Cannedbread on 2005-10-30
i am having the same problem, i tried pugging the perl files in /usr/lib/gaim and in ~/.gaim/plugins i also tried renaming them to .so files but that did nothing. gaim does not appear to be even looking at ~/.gaim/plugins so i have no idea what to do. ive tried many different plugins but none work.

---

