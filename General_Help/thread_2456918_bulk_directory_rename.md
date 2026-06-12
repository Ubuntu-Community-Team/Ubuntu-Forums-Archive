---
title: "bulk directory rename"
date: 2021-01-21
forum: General Help
---

### Post by cmcanulty on 2021-01-21
I am looking for a way to bulk rename directories. I prefer Graphical. I have hundreds of folders with [1] at the end of the folder name and would like an easy way to do this like remove the last 3 or however many characters . I tried caja rename which deleted the whole folders! didn't even send them to trash. gprename won't open except a blank white box. pyrenmer was great but has disappeared upon upgrade to 20.04, so sad. Thunar rename also won't seem to rename folders, only files. Of course I could be stupidly missing something. Thank you.

---

### Post by Holger_Gehrke on 2021-01-21
What version of Thunar are you using ? The bulk-rename in Thunar 1.6.15 on XUbuntu 18.04 will rename directories, at least it does for me if I select the directories (ctrl-s, enter '*[1]' into the form) and then start the renamer from the context menu and use the find-and-replace renaming method, set it to find '[1]' and leave the replacement field empty.

Holger

---

### Post by ajgreeny on 2021-01-21
Also have a try with gprename which you will have to install.
I assume it will work on folders as well as files, but I haven't used it for a very long time.

---

### Post by TheFu on 2021-01-21
**qmv** lets you use an editor - 2 columns - left is original name, right is the new name. If you are excellent with your editor of choice, this would be 10 seconds.

**rename** is a perl CLI tool. The regex matching would be funky for someone not used to perlre. There's a manpage about it (man perlre). Also, if the directories are all at the same level in the directory structure, that would make life a little easier.  What should happen if the target (new name) already exists?  That's a pretty big failure mode for any batch tool.
```
$ rename 's#\[1\]$##g'  bash-file-globbing-pattern
```
With rename, the first character after the 's' is the regex separator.  Often you'll see this as '/', but that can be confusing when other characters need to be escaped.  Another often-used alternate regex separator is '|'. That's pretty safe.  Metacharacters need to be escaped if you want them NOT to be used for the perlre meaning.

Or you could just create a list of all the directories you want using **find** - save that to a file.  Then create a **mv** script from that list.  That would have the most hands on - effectively doing what qmv does, just with more assurance.

```
mv 'old_name[1]'    old_name
mv 'really-old-name[1]'  really-old-name
...
``` I've used this to rename hundreds of files before someone here recommended qmv. ;)  qmv changed my life.

I'd use qmv with vim as my editor, but vim can do columnar edits freakishly fast once you know how-to do it.

---

### Post by simon-webb on 2021-01-21
[Edit]Whoops...I see someone's already suggested the rename tool while I was typing my suggestion!

Holger, that's great to know that Thunar's bulk renamer works when it's invoked from within Thunar. I've tended to launch it as a separate, standalone tool, and so like the OP I thought for some reason it didn't work with directories. Great to know that it does.

---

