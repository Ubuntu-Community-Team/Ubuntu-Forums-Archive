---
title: "[SOLVED] BASH script for renaming files"
date: 2007-09-14
forum: General Help
---

### Post by Tautoa on 2007-09-14
I've just started learning BASH scripting...not got very far yet, just a simple backup script. All my filenames tend to be mixed case and have spaces, which is a pain when manipulating files from the terminal (or in scripts). Is there any way I could create a script that would convert names to lowercase, and replace spaces with an underscore? It sounds easy, but I havn't found a way to do it yet...
Thanks :)

---

### Post by Rinzwind on 2007-09-14
for files in *.mp3; do mv "$files" `echo $files | tr ' ' '_'`; done

With this all files ending in .mp3 will have spaces converted into _.


for files in *.mp3; do mv "$files" `echo $files | tr '[:lower:]' '[:upper:]'`; done

same but lowercase into uppercase.

Or as you ask:

for files in *.mp3; do mv "$files" `echo $files | tr '[:upper:]' '[:lower:]'`; done

Upper into Lower.

---

### Post by Tautoa on 2007-09-14
Hehe, right, I'm gonna do that, and then I'm gonna figure out what it actually means :)
Is there a reason why its just for .mp3 files?

---

### Post by praet on 2007-09-14
the for files in *.mp3 is a filter to apply the changes to a subset of files only as an example.  You can of course apply no filter by using *.* or * as follows:

```
for files in *; do mv "$files" `echo $files | tr ' ' '_'`; done
```

Excellent post Rinzwind.

An explanation:
Its a basic for .. loop, taking files specified and performing an action to each.
Maybe presenting it this way with comments will help:
```

# for each filename with the mp3 extension.
for files in *.mp3  
   # mv - move the file (quotes around variable to allow for spaces in filename)
   # move to result of executable script between ``
   # inner script takes filename [echo $files]   and pipes the result to tr - translate program
   #    with arguments to change spaces to underscores [| tr ' ' '_'   ]
   do mv "$files" `echo $files | tr ' ' '_'`;
# goto next file
done

```

For more help you can read the manual entries for move and translate programs used.  ```
man mv
man tr
```

---

### Post by Tautoa on 2007-09-14
Ohhh, sorry, that was me being stupid...
When I read 'for files in *.mp3', I thought Rinzwind was explaining that it would only work for mp3 files... I didn't know it was part of the actual script!
Stupid mistake... It seems I have a long way to go :)
Now that you've explained that, the whole script makes sense to me.. I've never come across the translate program, but I get whats going on now.
Thanks to Rinzwind and praet :)

---

### Post by dscherry on 2007-09-14
Hi Tautoa,
You've probably already found some tutorials/help files, but this one is particularly well organized, and takes you to advanced topics in a logical manner...

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

hth,
Dan

---

### Post by Tautoa on 2007-09-14
Hi Dan, 
I've found a couple of helpful of web pages, but I like the look of the link you sent. It reminds me of the way I organised my A-Level notes, a series of plain text documents and a HTML contents page.
I seem to learn quicker that way, don't know why.
Thanks, I'm definitely going to use this site :)

---

