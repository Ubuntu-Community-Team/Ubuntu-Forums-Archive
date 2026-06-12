---
title: "How can I list UNIQUE files in Folder A versus Folder B?"
date: 2015-01-08
forum: General Help
---

### Post by NTL2009 on 2015-01-08
This is different from the usual 'find duplicate files' problem. I have a folder ("MAIN") which I _think_ contains all the pictures from my various sources. I have a bunch of other folders ("OLD"/ "X", "Y", "Z") which I _think_ I have have merged in to my MAIN folder, but I might have missed some. So if there are any unique filenames in "OLD", I would like to copy them to a TEMP folder (I'll decide where to move them later), and then delete the 'OLD' folders. 

The problem is that the directory structures are different, and I don't care about the path, I only care if the filename in OLD is unique to MAIN (regardless of position in either). More visually:

```

[FONT=courier new]MAIN       OLD
--/A       --/X   
  -pic1      -pic3
  -pic2    --/Y
  -pic3      -pic4 
--/B         -pic6
  -pic4
--C
  -pic5[/FONT]
```


In this case, I'd like to have the unique 'pic6' in OLD/Y copied to the first level of a TEMP folder. At that point, I can delete OLD, since I know it contains no unique files.

I didn't see any easy way to do the opposite of a duplicate search, maybe I'm missing something obvious? I could do a merge (rsync for example), but the different directory structures foils that plan.

TIA- NTL2009

---

### Post by dragonfly41 on 2015-01-08
I'm not sure whether meld might help

[http://meldmerge.org/help/folder-mode.html](http://meldmerge.org/help/folder-mode.html)

meld is in Ubuntu Software Centre

---

### Post by NTL2009 on 2015-01-08
Thanks, I tried MELD, but it highlights differences in the directory structure, so almost everything gets shown as a difference.

But what I'm really looking for is 'unique' filenames. I could have a thousand or more duplicates scattered across the file hierarchy. I just want to pull out the unique filenames from my 'OLD' folders.  

Maybe I need to pull the dir listings into a text files, strip all the path names (not sure how I'd do that - but I see they are all .jpg, so I can probably filter based on that - maybe 'ls -R -1 ?), then do a file comparison? I was thinking there might be something easier?

-NTL2009

---

### Post by Holger_Gehrke on 2015-01-08
Try
```

ls -1 <dir1>/ <dir2>/|sort|uniq

```
The output will contain the two directory names and all files which are not in both directories.

---

### Post by HermanAB on 2015-01-08
"ls -1 <dir1>/ <dir2>/|sort|uniq"

A brilliant example of the power of simple UNIX commands strung together the right way.

---

### Post by dragonfly41 on 2015-01-08
Must agree that the single line command is eloquent.
But just to return to meld for a moment ..
Surely this state points to a unique file in OLD directory

> 
States in folder comparisons

Each file or folder in a tree has its own state, telling you how it differed from its corresponding files/folders. The possible states are: 

...
New > **[COLOR=#008080]Green and bold[/COLOR]** > This file/folder exists in this folder, but not in the others. 
...



Just curious.

---

### Post by NTL2009 on 2015-01-08
> **Holger_Gehrke said:**
> Try
```

ls -1 <dir1>/ <dir2>/|sort|uniq

```
The output will contain the two directory names and all files which are not in both directories.

Yes, and thank you, I'm learning from your example (I added -R to make it dig down into the directory structure), but I'm looking for one step further. I tested this and it lists all files between the two, duplicates are listed only once - but what I am looking for is files that are unique to OLD only. Those would be the files that never got merged to my MAIN folder. I expect a large number of files unique to MAIN, as that is where I have been consolidating files from various sources. And each of my various sources will have many in common to MAIN - I'm looking for the ones in the sources that are NOT in MAIN.

Looking at my OP again - I want only 'pic6' as the output. It is unique to OLD. With the above code, I get each unique filename (listed only once, even for the duplicates - fine, but not what I need).  

> **dragonfly41 said:**
> Must agree that the single line command is eloquent.
But just to return to meld for a moment ..
Surely this state points to a unique file in OLD directory


Just curious.

The problem with that for me (unless I'm missing something), is that my directory trees are not matched. MELD was giving me every difference - so a common file, but under a different folder name shows as a 'difference'. But I don't care in this case - I have the file (image), so I can throw out the OLD at that point.

-NTL2009

---

### Post by NTL2009 on 2015-01-08
In Venn Diagram format:

[ATTACH]259108[/ATTACH]

-NTL2009

---

### Post by steeldriver on 2015-01-08
It's a bit oldschool (and possibly not very efficient) but you could simply find all the files under OLD and test whether you can find the same file (by name) under MAIN

```

$ while read -r -d $'\0' file; do [[ -n "$(find MAIN -name "${file##*/}")" ]] || echo "$file"; done < <(find OLD -type f -print0)  
OLD/Y/pic6

```

The code above just echoes the filename, but you should be able to replace the echo by any other operation on "$file".

---

### Post by NTL2009 on 2015-01-08
> **steeldriver said:**
> It's a bit oldschool (and possibly not very efficient) but you could simply find all the files under OLD and test whether you can find the same file (by name) under MAIN

```

$ while read -r -d $'\0' file; do [[ -n "$(find MAIN -name "${file##*/}")" ]] || echo "$file"; done < <(find OLD -type f -print0)  
OLD/Y/pic6

```

The code above just echoes the filename, but you should be able to replace the echo by any other operation on "$file".

OK, thanks, that is working as a starting point. I'll have to play with replacing the echo command, I'm not experienced with scripting, but I think I can figure out what I need. I'll take subsets of the 'OLD' folders to keep it manageable (and to avoid duplicates within the subsets) , and use this script to copy the selected unique files to a separate folder. Then I can check those folders and import them into my 'consolidated' image folder.

Then trash the OLD, which will all be redundant at that point.

I'm a little surprised there aren't some canned apps for this, I think many of us end up with multiple folders with dups and different file structures as we move files from one computer to another.

I'll come back and mark this 'SOLVED' after I've played some more, just in case I run into a problem. 

Thanks - NTL2009

---

### Post by NTL2009 on 2015-01-08
OK, so I made this small change to copy to a 'RESULT' folder, stripping the path to get just the files. It worked on my little test case, I'll try tomorrow on the real folders (~ 3,000 files in each, not huge, but not too unmanageable for this script I think). The echo script ran in less than ten minutes (I wasn't watching closely), so this should be good enough.

```
while read -r -d $'\0' file; do [[ -n "$(find MAIN -name "${file##*/}")" ]] || cp "$file" RESULT/"${file##*/}"; done < <(find OLD -type f -print0)
```

-NTL2009

---

### Post by Holger_Gehrke on 2015-01-09
A second attempt at this without looping over the files:
```

ls -1 old/ main/ main/|sort|uniq -u

```
By giving main **twice **I'm making sure everything from that directory is not unique; and passing the -u option to uniq makes it list **only **the uniq lines, instead of reducing the repeated lines.

---

### Post by steeldriver on 2015-01-09
Another thought from me ...

```

$ awk -F\/ '$1=="MAIN" {MAIN[$NF]=$0; next;}; !($NF in MAIN)' < <(find MAIN OLD -type f)
OLD/Y/pic6

```

---

### Post by NTL2009 on 2015-01-10
> **Holger_Gehrke said:**
> A second attempt at this without looping over the files:
```

ls -1 old/ main/ main/|sort|uniq -u

```
By giving main **twice **I'm making sure everything from that directory is not unique; and passing the -u option to uniq makes it list **only **the uniq lines, instead of reducing the repeated lines.

That one didn't seem to work for me. I got:

OLD/:X
Y

Making it recursive (adding -R) gave me:

OLD/:
OLD/X:
OLD/Y:
pic6
X
Y




> **steeldriver said:**
> Another thought from me ...

```

$ awk -F\/ '$1=="MAIN" {MAIN[$NF]=$0; next;}; !($NF in MAIN)' < <(find MAIN OLD -type f)
OLD/Y/pic6

```

That also worked. I didn't test it on a larger dir to check speed.


This was helpful, and I learned a few tricks along the way. Bad news is I found duplicate names on images that were different (a camera we used got reset and repeated image names, or two cameras had the same sequence). So I had to do some manual tweaking to really get this done, but these scripts did help for part of it.

Marking it SOLVED since these scripts do the job I asked for. Thanks all!

-NTL2009

---

