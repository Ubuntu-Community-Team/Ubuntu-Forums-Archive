---
title: "Rename multiple files using command line"
date: 2023-03-13
forum: General Help
---

### Post by bjngchn on 2023-03-13
Let's say I have lots of files  whose names all starting with (or containing )  the same useless string of characters and I  want to erase them  all uniformly, inside a directory. Not talking about the extension, just file names.  For example I have QWEfish.mp3 , QWElion.mp3 QWEchicken.mp3 , and I want to erase QWE by replcing all QWE with empty string, or a better  string of characters. I want to get fish.mp3, lion.mp3, chicken.mp3, as the result.

---

### Post by TheFu on 2023-03-13
Linux/Unix doesn't care about extensions. Those are just for humans.

The '**rename**' tool allows regex pattern matching.
```
rename 's/^QWE//g' QWE*
```

There are other bulk renamers too.
For a small number of files, I'll often use **qmv** which opens the list of files into my editor of choice where I can modify the filenames as I like, use visual selections, search and replace, or just remove parts of filename.

---

### Post by bjngchn on 2023-03-14
Thanks, and DOLPHIN file manager program also have RENAME option. I knew it existed, but it seems to work for multiple files as well. Can we do the same thing with doplhin?

---

### Post by bjngchn on 2023-03-14
Got syntax error with this code. Not sure why. Installed rename first.  Tried commands here: [https://phoenixnap.com/kb/rename-file-linux](https://phoenixnap.com/kb/rename-file-linux)  also, none worked. Some worked for 1 letter only.  Maybe I have a different version of rename program? Installed with sudo  Edit: finally one of commands worked, not sure why worked this time and failed at other times.

---

### Post by bjngchn on 2023-03-14
Still can't erase:  [] -  Do these characters need special treatment? ALSO want to be able to do this recursively in subdirectories also.

---

### Post by TheFu on 2023-03-14
> **bjngchn said:**
> Thanks, and DOLPHIN file manager program also have RENAME option. I knew it existed, but it seems to work for multiple files as well. Can we do the same thing with doplhin?

I don't use doplhin, so wouldn't know.

The provided rename command will work with the example files, as shown.
rename has been around 30 yrs. I don't think it has changed. It uses perl regex.  All regex engines have special characters with special meaning, in specific situations.  Regex patterns are very powerful, but you have to learn them.  Think **egrep/sed** patterns.  I think there are regex online testing tools where you can check the pattern you create. 

Saying a command doesn't work, but not showing the exact command used isn't helpful.

Recursively moving files is dangerous. Bad things often happen.

---

### Post by Holger_Gehrke on 2023-03-14
'rename' uses Perl-expressions. By far the most useful of these is the substitution which has the form **'s/regular expression for text to be substituted/text to be substituted/'**. In a regular expression several characters have special meaning. You can find an explanation of these in the manual page for 'regex' in section 7 of the manual ('man 7 regex'). Perl regular expressions are slightly different from standard REs and there is a separate manual page for them IIRC but you would need to install the package with the Perl documentation to find that. In both standard and Perl REs the characters '[' and ']' enclose members of a group of characters you expect in this place. So for example the RE 'M[ae][iy]e?r' would match all the various ways of writing the name 'Maier'/'Mayer'/'Meier'/'Meyer'/'Mair'/'Mayr'/'Meir'/'Meyr' (the '?' in the expression is a quantifier meaning the preceding sub-expression is optional and can occur 0 or 1 times). 

If you want to **take away the special meaning** of a character you have to **prefix** it **with a backslash**. So for example "rename 's/\[.*\]//' *" would substitute the empty string for everything from the first '[' to the last ']' in a filename (the '.' has the special meaning of 'any character' and the '*' is another quantifier, meaning 'zero or more times'; this means if you need to match a literal period you should write '\.' in an RE - but since the non-escaped '.' does match a period (or anything else) it's one of the more subtle errors you can make when writing REs).

Holger

---

