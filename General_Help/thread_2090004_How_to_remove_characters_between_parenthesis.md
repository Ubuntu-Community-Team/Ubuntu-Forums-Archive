---
title: "How to remove characters between parenthesis"
date: 2012-11-30
forum: General Help
---

### Post by altjx on 2012-11-30
I've just came from Windows 8 and having a huge issue right now. I used FileHistory to back up my data to an external hard drive, and now all of my files have been backed up in addition to appending a timestamp in the file name.

I am in need of removing everything between parenthesis that starts off with "(2012_" and ends with ")".

Can anyone help me with this?

Any help would be greatly appreciated.

Thanks,

---

### Post by gnusci on 2012-11-30
Try

$ ll | grep -v "2012"

You&#8217;ll get the idea.

---

### Post by altjx on 2012-11-30
Again, any help with common sense would be greatly appreciated.

---

### Post by steeldriver on 2012-11-30
are you wanting to rename all the files - removing the timestamps? if so, that should be possible using the 'rename' command with a regular expression something like

```
rename -nv 's/ \(2012_.*?\)//' *
```[note: I've included the space in front of the left parenthesis]

The '-v' makes it verbose (tells you about each replacement) and the '-n' makes it take no action - leave this in until you're SURE it's doing the right thing - IN PARTICULAR be careful about files getting overwritten if there's any possibility that the resulting filenames are non-unique

Hope this helps

---

### Post by gnusci on 2012-11-30
What about this:

$ cat FileHistory | sed -e 's/\((2012.*\)//g'

---

### Post by altjx on 2012-11-30
> **steeldriver said:**
> are you wanting to rename all the files - removing the timestamps? if so, that should be possible using the 'rename' command with a regular expression something like

```
rename -nv 's/ \(2012_.*?\)//' *
```[note: I've included the space in front of the left parenthesis]

The '-v' makes it verbose (tells you about each replacement) and the '-n' makes it take no action - leave this in until you're SURE it's doing the right thing - IN PARTICULAR be careful about files getting overwritten if there's any possibility that the resulting filenames are non-unique

Hope this helps

Nice man. Thanks very much! This helped! I am sure I can figure out a way for it to become recursive now :). Again, thanks a LOT!!!

EDIT: nevermind. I thought it would be easy... but now I'm not sure how to do this recursively.

---

### Post by altjx on 2012-11-30
FileHistory?

---

### Post by steeldriver on 2012-11-30
Happy to help

You can use 'find' to descend recursively and put the rename into an exec action - or more robustly you could use a while - read from a find, something like

```
while read -r -d $'\0' file; do rename -nv 's/ \(2012_.*?\)//' "$file"; done < <(find . -type f -print0)
```Alternatively you might be able to just use recursive shell globbing,

```
shopt -s globstar; rename -nv 's/ \(2012_.*?\)//' **/*
```Whichever route you go, you might want to change the . (any character) to [^\/] (any character except literal /) to make sure it applies the match strictly to the filename portion, i.e.

```
's/ **\(2012_[^\/]*?\)**//'
```

---

### Post by altjx on 2012-11-30
> **steeldriver said:**
> Happy to help

You can use 'find' to descend recursively and put the rename into an exec action - or more robustly you could use a while - read from a find, something like

```
while read -r -d $'\0' file; do rename -nv 's/ \(2012_.*?\)//' "$file"; done < <(find . -type f -print0)
```Alternatively you might be able to just use recursive shell globbing,

```
shopt -s globstar; rename -nv 's/ \(2012_.*?\)//' **/*
```Whichever route you go, you might want to change the . (any character) to [^\/] (any character except literal /) to make sure it applies the match strictly to the filename portion, i.e.

```
's/ **\(2012_[^\/]*?\)**//'
```

Very nice! The first piece of code solved my issue. Can't wait to learn more about this. Thanks again man. Very much appreciated. You have no idea :)

---

