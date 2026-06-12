---
title: "Compress filenames containing spaces using zip"
date: 2022-10-11
forum: General Help
---

### Post by raleigh3 on 2022-10-11
I needed to  rename some .png files uses only spaces and no file extensions.

They still work as icons.

However, no zip does not zip them.

Any fix?

---

### Post by vanadium on 2022-10-12
Not sure what you actually tried, but it should not be a problem to compress files that have spaces in the file name. If they don't, the fix will be to rename the files.

---

### Post by HermanAB on 2022-10-12
Normally, “spa ces” are delimiters.  On the command line, use quotes, to ensure that names with spaces are included.

With a GUI, just highlight and right click to select compress.

---

### Post by TheFu on 2022-10-12
This is why I don't allow spaces in filenames or directory names.  When I see a name with a space, I immediately fix it - replacing the {space} with an '_'.

I use 'rename' to do this and have a tiny script to do things the way I like. 
```
#!/bin/sh

IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/[_]+/_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*
rename 's/_2022/-2022/g' $IN*

```
This let's me rename files fast.

For example, 
```
$ ren-fav [A-Z]
```
will rename all files starting with uppercase.
```
$ ren-fav 4
```
will rename all files starting with a '4'.

---

### Post by raleigh3 on 2022-10-12
Could you give me an example?

Thanks.

---

### Post by raleigh3 on 2022-10-12
Here are some more details. 

I dragged some .png files to my desktop. They show some keyboard shortcuts.

I wanted to get rid of the text under those icons.

I discovered that using filenames with only spaces and no extension got rid of all the text except the file size.

---

### Post by ajgreeny on 2022-10-12
I use Xubuntu with Xfce and make use of a very handy ***rename 's/\ /_/g' %F*** command in the file manager thunar's Custom Actions utility.

It does the same as TheFu's script and save me a huge amount of time and hassle by avoiding spaces in any file or folder names.
I can simply highlight all the files in any folder (not any system files out of my home of course) right click in them and choose **Remove Spaces** from the context menu and every space is replaced with an underscore.
Any files that do not have spaces in names are ignored of course, so it does not need all files in the folder to contain spaces.

I don't know mate well enough but there may be a similar method where you could do the same or you could simply use TheFu's script.

---

### Post by TheFu on 2022-10-12
> **raleigh3 said:**
> Could you give me an example?

Thanks.

Who? Example of what?

ajgreeny's file manager customization doesn't do the same thing, but it is probably close enough for most people. A, you need to be using a file manager that allows customization actions.  I don't.
You need to be happy with _-_ in names.  I'm not.
I never want the current year in filenames to have a leading _ either.  I want " 2022" to be "-2022", always.
And I don't want to pass in full filenames or do globbing.  This is a little non-standard, so I can understand why people wouldn't like this, but I rename files ALL-THE-TIME and saving 2 keystrokes is a big thing.  

OTOH, once a file is renamed, every script/progam, no matter how poorly written, will work.  I think that's the root issue you are seeing.  Your intent and the way the system handles filenames don't match.  You could change the IPS character in your shell, but that's usually worse than living with the issue and the real convenience of having a {space} as a filename delimiter. But sometimes a {space} isn't good, not often on my systems, but we all have different ways of working.

---

### Post by #&amp;thj^% on 2022-10-12
> **TheFu said:**
> This is a little non-standard, so I can understand why people wouldn't like this, but I rename files ALL-THE-TIME and saving 2 keystrokes is a big thing.  

OTOH, once a file is renamed, every script/progam, no matter how poorly written, will work.  I think that's the root issue you are seeing.  Your intent and the way the system handles filenames don't match.  You could change the IPS character in your shell, but that's usually worse than living with the issue and the real convenience of having a {space} as a filename delimiter. But sometimes a {space} isn't good, not often on my systems, but we all have different ways of working.
I had to stop by and Thank TheFu, I like this one better than my old defunct method.
I was leaving out Authors and Site Ip's(Source address) before.
If I  would slow down long enough, and put some thought into my scripts, I'd be more fulfilled..LOL
EDIT: I left this out:
> **TheFu said:**
> This is why I don't allow spaces in filenames or directory names.  When I see a name with a space, I immediately fix it - replacing the {space} with an '_'.

I use 'rename' to do this and have a tiny script to do things the way I like. 
```
#!/bin/sh

IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/[_]+/_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*
rename 's/_2022/-2022/g' $IN*

```


---

### Post by TheFu on 2022-10-12
1fallen, there are some subtle things that aren't clear in my script.  It works on groups of files, not 1 file at a time, in a loop. the order of the 'rename' commands is important.  Also, not specifying any {spaces} the input is very important, since the rename commands won't handle that well.

Subtle things matter.

---

### Post by #&amp;thj^% on 2022-10-13
> **TheFu said:**
> 1fallen, there are some subtle things that aren't clear in my script.  It works on groups of files, not 1 file at a time, in a loop. the order of the 'rename' commands is important.  Also, not specifying any {spaces} the input is very important, since the rename commands won't handle that well.

Subtle things matter.

Thanks for that information, I already knew that. :) (None the less good information for this thread)
> **TheFu said:**
> This is why I don't allow spaces in filenames or directory names.  When I see a name with a space, I immediately fix it - replacing the {space} with an '_'.

I use 'rename' to do this and have a tiny script to do things the way I like. 

I picked that up on your examples shown above


I'm doing some changes and will post back anything relevant.
That's why I said "If I'd slow down long enough"
Still a good script though.

---

