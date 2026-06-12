---
title: "How to harvest files from several directories - CLI"
date: 2013-05-28
forum: General Help
---

### Post by zenfunk on 2013-05-28
Hi everyone,
I'm in the process oflearning Bash scripting. Right now I want to harvest all the .png files from several subfolders (all are in one master folder) and put them all in one target folder. I played a bit with ls -R and grep *.png, but this aparently gets me nowhere. I know there must be a simple solution, but I seem to lack the skills. Could anyone of you commandline ninjas show me towards the right direction?
Thank you very much in advance,
Christian

---

### Post by HiImTye on 2013-05-28
```
for f in /path/to/folder1/*.png /path/to/folder2/*.png /path/to/folder3/*.png; do
# cp $f
# mv $f
done
```
replace the folders with the ones you want. if you want to copy, remove the # before cp; the # before mv for move
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by zenfunk on 2013-05-28
> **HiImTye said:**
> ```
for f in /path/to/folder1/*.png /path/to/folder2/*.png /path/to/folder3/*.png; do
# cp $f
# mv $f
done
```
replace the folders with the ones you want. if you want to copy, remove the # before cp; the # before mv for move

Brilliant. Is there a way to look into these folders recursively? So I only have to specify the main folder, not each individual subfolder?

Thanks for your efforts,
Christian

---

### Post by HermanAB on 2013-05-29
Howdy,

Learn how to use the 'find' command, with the 'exec' option. Read the man page.

The reason why Bash looping is so cripple, is because 'find' does it all.

---

### Post by HiImTye on 2013-05-29
> **HiImTye said:**
> ```
for f in /path/to/folder1/*.png /path/to/folder2/*.png /path/to/folder3/*.png; do
# cp $f
# mv $f
done
```
replace the folders with the ones you want. if you want to copy, remove the # before cp; the # before mv for move


helps if I have an out folder, should be
```
out="/path/to/folder"
for f in /path/to/folder1/*.png /path/to/folder2/*.png /path/to/folder3/*.png; do
#cp "$f" "$out"
#mv "$f" "$out"
done
```for recursive, use something like
```
in="/path/to/folder1/
/path/to/folder2/
/path/to/folder3/"
out="/path/to/folder"
while read -r f; do
#cp -R "$f" "$out"
#mv -R "$f" "$out"
done< <(echo -e "$test")
```
if you're saving them as scripts then set out to "$1" and in to "$2" then execute them as
```
scriptName "/path/to/folder anywhere"
#-- or --
scriptName "/path/to/folder anywhere" "/path/to/folder1
/path/to/folder2
/path/to/folder3"
```
lastly, if you're saving scripts, it's a good idea to make line 1
```
#!/bin/bash
``` 

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by HiImTye on 2013-05-29
> **HermanAB said:**
> Howdy,

Learn how to use the 'find' command, with the 'exec' option. Read the man page.

The reason why Bash looping is so cripple, is because 'find' does it all.

I prefer locate, it's faster, and bash is anything but crippled if you know how to use it. Linux commands work the Unix way, "do one thing, really well" because you can redirect their output
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Vaphell on 2013-05-29
*find* is **the** tool for file search and manipulation of the results, there is nothing better.

```
mkdir /dest/dir
find /src/dir -iname '*.png' -exec mv '{}' /dest/dir \;
```

---

### Post by HiImTye on 2013-05-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I prefer the speed of
```
mkdir /out/dir/
locate --regex '/path/to/wherever/.*.png' '/path/to/wherever else/.*.png' | while read f; do mv "$f" /out/dir/; done
```
which takes about a half second, compared to a half minute with find

---

### Post by Vaphell on 2013-05-29
and what if the database that *locate* uses is not up to date? *find* doesn't care about it.

---

### Post by Grenage on 2013-05-29
Indeed, when it comes to handling files across directories, *find* is the tool I use the most - by far.

---

### Post by HermanAB on 2013-05-29
You got to learn how to use 'find'.  Locate only searches for things, it cannot execute commands.  If you know how to use find, then you almost never need to use a loop.

---

### Post by HiImTye on 2013-05-29
> **Vaphell said:**
> and what if the database that *locate* uses is not up to date? *find* doesn't care about it.

you can make a tempdb, here's some examples  [http://ubuntuforums.org/showthread.php?t=2109455](http://ubuntuforums.org/showthread.php?t=2109455) (either of the cleanFilenames scripts)
you could easily alias the updatedb command to feed it a set of folders
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

