---
title: "assigning pwd to a variable"
date: 2012-12-29
forum: General Help
---

### Post by howhy on 2012-12-29
well since I am a beginner today I learnt how to change permission recursively of files and folder in a directory

using 'find foldername -exec chmod 788 {} \;'

what i want to know how can i set a variable to pwd so that i got a directry and using a defined alias it changes the permissions of the directry contents?

---

### Post by steeldriver on 2012-12-29
1. If you want to execute 'find' relative to the current directory you can just use '.'

```
find . -name 'whatever' -type f
```2. To assign a variable would be something like

```
d="/path/to/dir"; find "$d" -name 'whatever' -type f
```3. To assign and use the pwd would be

```
d=$(pwd); find "$d" -name 'whatever' -type f
```but see (1)

Be careful with recursive chmods... also 7**88** is not a valid **octal** mode

PS chmod has a recursive mode built in - see [FONT=Courier New]man chmod[/FONT] - although the value of using 'find' is that you can apply it selectively (based on name, file type etc.)

---

### Post by Vaphell on 2012-12-29
also bash provides you with the $PWD variable that doesn't require runnning *pwd*

> be careful with recursive chmods... also 788 is not a valid octal mode

true that
most likely you want separate chmods for files and dirs which requires *find -type d/-type f*
if you want full access for dirs and read/write for files you need 7/+rwx eg 755 or 700, etc for dirs and 6/+rw for files, eg 644 or 600 etc.
Personally i like to use +/-rwx notation, which allows to add remove a single permission without setting 2 others like in case of numeric notation.

---

### Post by howhy on 2012-12-29
i have made an alias in .bashrc chmods with directory as 
d=$(pwd);
alias chmods='find "$d" -exec chmod 755 {} \;'

but if it try to run from terminal with sudo i get error saying
 sudo: chmods: command not found

---

