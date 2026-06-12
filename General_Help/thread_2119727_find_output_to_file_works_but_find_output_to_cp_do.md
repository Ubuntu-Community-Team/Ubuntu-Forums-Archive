---
title: "find output to file works but find output to cp doesn't copy all files in output"
date: 2013-02-24
forum: General Help
---

### Post by twinturbotom on 2013-02-24
Using the command below I find multiple files and output  names to a file.

```
find -iname "*pdf" -o -iname "*docx" -o -iname "*doc" -o -iname "*string*" -o -iname "*ppt" -o -name "*pptx" > ~/Documents/LIST_OF_COPIED

```I then attempt to copy the same found files to another directory and notice that some of the files are not copied!

```
find -iname "*pdf" -o -iname "*docx" -o -iname "*doc" -o -iname  "*STRING*" -o -iname "*ppt" -o -name "*pptx" -exec cp -R -u --parents -t  ~/Documents/TARGET_DIRECTORY/ {} \;
```Seems like directories that should have multiple files only have 1.  Also directories and files starting with numbers aren't copied.  Some of these files have spaces as well.

With the "LIST_OF_COPIED" document looking right I take it my find output is fine.  I'm missing something for the cp command.

Thoughts?

Thanks.

---

### Post by twinturbotom on 2013-02-24
I was able to copy more files with xargs, still falling short on directories and files starting with numbers.  Latest code:
```

find -iname "*pdf" -o -iname "*docx" -o -iname "*doc" -o -iname "*STRING*" -o -iname "*ppt" -o -name "*pptx" | xargs -i  cp {} --parents -Rft ~/Documents/TARGET_DIRECTORY/
```

---

### Post by erind on 2013-02-27
> **twinturbotom said:**
> [...]

Seems like directories that should have multiple files only have 1.  Also directories and files starting with numbers aren't copied.  Some of these files have spaces as well.

With the "LIST_OF_COPIED" document looking right I take it my find output is fine.  I'm missing something for the cp command.

Thoughts?

Thanks.
"*find*" is very picky in its syntax, and it's the grouping ( round parens below ) that made your code fail:

```
*cd* [I]/path/to/dir
[/I]find . **[COLOR=Red]\([/COLOR] **-iname "*pdf" -o -iname "*docx" ... -o -iname "*STRING*" **[COLOR=Red]\)[/COLOR]** -exec cp -R -u --parents -t ~/Documents/TARGET_DIRECTORY/ {} **+**

# Note grouping, the path and the '+' modifier at the end.
# with xargs 

*cd* */path/to/dir*
find . [COLOR=Red]**\(**[/COLOR] -iname "*pdf" -o -iname "*docx" ... -o -iname "*STRING*" **[COLOR=Red]\)[/COLOR]** -print0 | xargs -0 cp --parents -Rft ~/Documents/TARGET_DIRECTORY/

```I'd suggest to check **rsync**, as it's a much more powerful copy tool.

---

### Post by twinturbotom on 2013-02-27
Thanks for the explanation and direction.  I'm pretty new and really need to not only get a handle on base tool usage & syntax but what other options and commands are available to perform tasks cleaner... Like rsync in this case.

Thanks.

---

### Post by erind on 2013-02-27
With **rsync** it'd be something like this:
```
cd /path/to/dir

find . \( -iname "*pdf" -o -iname "*docx" ... -o -iname "*STRING*" \) -print0 | rsync -avr0 --files-from=- . ~/Documents/TARGET_DIRECTORY/ 
```Check here:
[http://ubuntuforums.org/showthread.php?t=2100708](http://ubuntuforums.org/showthread.php?t=2100708)
[B]
rsync [/B]has also the ability to read from a list of files ( *--files-from=file_lis*t ), which **find** *doesn't support*.

This page has plenty of examples on find usage:
[http://www.softpanorama.org/Tools/Find/index.shtml](http://www.softpanorama.org/Tools/Find/index.shtml)

---

