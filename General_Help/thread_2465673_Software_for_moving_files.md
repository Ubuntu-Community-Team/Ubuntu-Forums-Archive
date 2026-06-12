---
title: "Software for moving files"
date: 2021-08-08
forum: General Help
---

### Post by david1992 on 2021-08-08
Hi guys. I am looking for a software which can move seleced files to new folders with same name. For instance if I have the following files

note1.txt
note12.txt
note41.txt
note0011.txt

I want to that files be moved to the folders with exact name.


On Windows OS similar software is Files2Folder but because I don't use Windows OS anymore I am asking you for the name.

---

### Post by TheFu on 2021-08-08
mv?  Is this a trick question?
```
mv note* ~/new-folder/named/this/
```
Any file manager can do it too.  Nautilus, thunar, caja, .... 

If there are problems, it is likely to be permissions.  Unix permissions can't automatically be walked over or there wouldn't be any point. Normally "Permission Denied" or ERROR 13 result if the problem is with permissions.

---

### Post by mIk3_08 on 2021-08-08
Ubuntu 18.04 has already that kind of functions; the right click move to options. You just have to add Folder Bookmarks in your nautilus for more easy access to the Folder you wanted to move your Files.
Its is more convenience and nice to navigate. Very smooth in transferring files.  It is also user friendly in way of organizing your files.
You just have to highlight your files and right click then choose "move to" option then select where you want to place you files at the bookmarks.  
That's it, Good Luck!

---

### Post by david1992 on 2021-08-08
Thank you both for the replies but you didn't understand me completly.
If I have in folder these files
[COLOR=#000000]note1.txt[/COLOR]
[COLOR=#000000]note12.txt[/COLOR]
[COLOR=#000000]note41.txt[/COLOR]
[COLOR=#000000]note0011.txt[/COLOR]

I want to each one be moved in the folder with same name.

For instance 
note1.txt will be moved to note1 folder
note12.txt will be moved to note12 folder
note41.txt will be moved to note41 folder
note0011.txt will be moved to note0011 folder

---

### Post by yancek on 2021-08-08
The command in post 2 tells you how to do this manually, one file at a time.  If that is what you want, you will need to enter the full path of the directory you are copying to.  If your new folders, the ones you want to copy to are in the same directory, you won't need the full path, just the name of the folder. 

I'm not really sure what you want, software that will detect the name of the file and copy it to a folder of the same name?  If that's it, I don't know any software that will do that but it may exist.

---

### Post by dragonfly41 on 2021-08-08
Krusader dual-pane file manager allows UserActions to be written 
based on variables such as filename, filepath, fileextension etc.

It is quite a powerful feature. I have written a number of UserActions to support my various workflows.

[P.S.] I now remember an alternative, perhaps simpler. KRename.

---

### Post by Impavidus on 2021-08-08
If the software doesn't exist yet, it's time for some scripting. I see that you don't want to give the directory the same name as the files, as you want to strip the extension.

Take the filename, strip the extension. Handle the case when the filename has no extension; you may have to rename the file to a temporary name. Create the directory if it doesn't exist yet. Handle the error if you can't create the directory. Handle the case when the file already exists in that directory. Move the file. Handle the error if moving fails.

---

### Post by TheFu on 2021-08-08
It would be a 2-3 line script.  Google will find one, probably on stack-exchange. Let's check my google-fu:
[https://stackoverflow.com/questions/55734576/create-subfolder-with-same-name-as-parent-and-move-files-into-it](https://stackoverflow.com/questions/55734576/create-subfolder-with-same-name-as-parent-and-move-files-into-it)
My search terms were: "mv files into same named subdirectory"
```
for file in */a.txt ; do 
    dir=${file%/a.txt}
    mkdir "$dir/$dir"
    mv "$file" "$dir/$dir"
done
```
That's not a complete script. There are lots of ways to remove the extension in bash.
ROOT=${1/%.txt/}
so, if $1 is foo.txt, then $ROOT would have "foo" as the value.

```
#!/bin/bash
for filename in "$@"; do
  ROOT=${filename/%.txt/}
  mkdir -p "$ROOT"
  mv "$filename" "$ROOT"
done
```
That is a filter, so any files passed to the stdin special file can be handled.  The accepted solution has some issues that I can see and no error checking.  
Run it:
```
$ ./filter *txt
```

Yep. It works.  There are all sorts of things you can do to make it easily available system-wide and from GUIs.
[LIST]
[*]Make the script have execute privileges
[*]Place the script into a directory in your $PATH.  I like to use ~/bin/, but /usr/local/bin/ could work too.
[/LIST]

Beware that extensions on Unix systems are for humans, not programs.  Programs don't care - except a few poorly written ones. If a filename doesn't have an extension, but is passed into the script via globbing, some collisions can happen.  Yes, the script above is part of the "few poorly written ones."

There will be some issues worth fixing.  [https://tldp.org/LDP/abs/html/abs-guide.html](https://tldp.org/LDP/abs/html/abs-guide.html) should have examples.
I didn't follow scripting best practices - like error checking, looking for name collisions and using the full-path for all external programs used.  For a quick script like this, I probably wouldn't. If it were for a client, it would be 10x longer with all those protections.

---

### Post by TheFu on 2021-08-08
And my script doesn't like files or directories with spaces or odd characters in the names.  To get around that, either rename the files or pass in the names fully quoted or use the filter capabilities to have another program feed the names, 1 at a time.

The 
```
for filename in "$@"; do
```
loop, splits names using whitespace. I suppose some other character could be use, perhaps the '^'?  IFS is the variable to be changed, I think.  You'll want to look that up.

---

### Post by mIk3_08 on 2021-08-09
> **david1992 said:**
> 
note1.txt will be moved to note1 folder
note12.txt will be moved to note12 folder
note41.txt will be moved to note41 folder
note0011.txt will be moved to note0011 folder

Wow! this is a powerful application tool for quick naming folder. The document name is move to the equal folder name.
This is for quick folder naming and organizer, cool. I haven't encounter this yet. But maybe soon. :-D here in Linux Ubuntu. :-)

---

