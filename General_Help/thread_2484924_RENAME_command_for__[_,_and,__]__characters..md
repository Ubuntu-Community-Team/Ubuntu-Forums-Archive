---
title: "RENAME command for  [ , and,  ]  characters."
date: 2023-03-14
forum: General Help
---

### Post by bjngchn on 2023-03-14
Managed to use rename command to edit file names of several files in a directory at once.   But can't remove/replace  the following character:  [ (square bracket)   Any trick to edit it also?   (Maybe  YT downloaders are adding them intentionally to protect their site urls inside filenames).

---

### Post by The Cog on 2023-03-14
'[' has special meaning to the pattern matching code (introducing a set of possible matching characters). Try preceding it with a backslash, e.g. "abc\[def".

---

### Post by bjngchn on 2023-03-14
Thanks, Found a similar answer, worked for one half of bracket failed for other half.

Anyway, found a command which worked in this special case:

find . -depth -name '*\[*\]*' -type f -exec rename -v -d 's/^\[.*?\]//s' {} +

(recursively removing square brackets and anything inside those square  brackets)

source : 
unix.stackexchange .com/questions/728584/recursively-remove-square-brackets-and-their-surrounded-contents-from-file-name

---

### Post by bjngchn on 2023-03-14
Also would appreciate a command which finds the first - character (and only the first one),
and ERASES that character and anything that comes BEFORE that character.

---

### Post by TheFu on 2023-03-14
> **bjngchn said:**
> Also would appreciate a command which finds the first - character (and only the first one),
and ERASES that character and anything that comes BEFORE that character.

```
rename 's/^.//g'  file-glob-pattern
```
That will remove the first character in all the files/directories which match the file-glob-pattern.

You'll need to be more specific on what you mean by "character", since anything that can be typed or seen/unseen is a "character".  Do you mean digit or ACSII English alphabet?  That's a specific type of character.

---

### Post by bjngchn on 2023-03-14
Thanks. I typed which character I meant:  Hypen  Dash  -    I want to be able to erase the first hypen character and anything that comes before it.

---

### Post by TheFu on 2023-03-14
> **bjngchn said:**
> Thanks. I typed which character I meant:  Hypen  Dash  -    I want to be able to erase the first hypen character and anything that comes before it.

```
rename 's/^.*[-]//g'  file-glob-pattern
```

There are other ways too, but for most people using a file manager is easiest.  If a filenane/directory name starts with a "-something", that usually requires an added option from other commands (like mv, cp, etc.) to convince the command it isn't an option.  [https://unix.stackexchange.com/questions/367363/remove-leading-characters-in-filename-up-to-a-certain-pattern](https://unix.stackexchange.com/questions/367363/remove-leading-characters-in-filename-up-to-a-certain-pattern) shows an example where the -- option is passed to ensure the command know that the remaining arguments are files.

hyphens have special mean in regex.  The '^' does too - it has 2 different meanings depending on context. Some punchuation and special ASCII characters also have special meaning.

---

