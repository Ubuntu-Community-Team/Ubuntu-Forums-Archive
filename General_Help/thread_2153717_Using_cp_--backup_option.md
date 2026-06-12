---
title: "Using cp --backup option"
date: 2013-06-12
forum: General Help
---

### Post by cogset on 2013-06-12
I've just tried to use the **cp --backup** option to copy some folders from a backup drive to another folder:these all share the same name (on the backup drive they are nested inside other progressively named folders),so I'm searching for a way to group them in a single folder without overwriting each file.
The **cp --backup=numbered **option works with files but not directories,and produces an output like that```
 folder.~1~
```which is kinda inconvenient for me as it makes the backup copies hidden:is there a way to control this string,tweaking it to something more usable likefolder_1,folder_2and so on,or at least skip the dot  ?
And,more importantly,is there a way to make it work on directories as it does on files ?

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
cp -R --backup=numbered --suffix=_ /in/path/ /out/path/
```might be what you're after, or you could just exclude existing files
```
cp -R -n /in/path/ /out/path/
```

---

### Post by cogset on 2013-06-12
This is more complicated that I thought it would be : using the **cp -R --backup=numbered **command kinda works,but actually copies/backups the *content* of the directories instead of the directories themselves,which is what I'm after.
Also,the** --suffix= **option instead of automatically creating a numbered series of backups with the string** .~n~ ,**creates just one backup and then keeps overwriting it at every retry.

Edit:I've also experimented with rsync and its --backup option getting the same behaviour,only the files inside the directories are backed up,not the directories.

Since I need to move a number of directories all named "session" in a single folder and have them renamed like session_1,session_2 or something like that,how can I accomplish this ?

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you would need to write a script. something like
```

for d in /path/to/folder1 /path/to/folder2 /path/to/folder3; do
 set $((i++))
 cp -R "$d" /out/path/foldername_"$i"
done
```

---

### Post by cogset on 2013-06-13
Sorry if keep going around this:apart from using a custom script,isn't there any native tool/command/option in Linux that allows to copy/backup actual directories instead of merging their contents?
I'm asking because,by the looks of it,what I'm getting with **cp -r --backup=numbered** is what I would get in the GUI if I tried to copy or drop a directory in a location where there is already an identically named directory.
There should be (at least,I hope) some way to get around this with a command instead of writing a specific script - Windows (as far as I can remember) can do this,it would be IMHO kinda weird if Linux could not.
At this point,what I'm left to would be to manually copy each of these identically named directories to a temporary location one at the time,rename each one and then finally move them  to their new location-hardly a smooth sailing...

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
there are backup utilities, which I don't have a lot of experience with. you could just take the script I used above and make it a utility by using command line input, such as```
#!/bin/bash
if [ -z "$2" ]; then
 P="$PWD"
else
 P="$2"
fi
if [ -z "$3" ]; then
 F="${1##*/}"
else
 F="$3"
fi
echo "$1" | while read -r d; do
 if [ -d "$d" ]; then
  set $((i++))
  cp -R "$d" "$P/$F"_"$i"
 fi
done
```

---

### Post by cogset on 2013-06-15
Thanks a lot,that's too complicated at this stage for me,so for now manual renaming/moving it is.

---

