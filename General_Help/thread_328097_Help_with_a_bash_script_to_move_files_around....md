---
title: "Help with a bash script to move files around..."
date: 2006-12-30
forum: General Help
---

### Post by viciouslime on 2006-12-30
Could anybody help me create (point me to a similar one I can modify, or indeed write one for me :D ) a script that will scan through a directory and its subdirectories and then move every file it finds up by two directories.

My Music collection has worked itself into a bit of a mess after converting it to ogg vorbis. For example: /home/dan/Music/Brian May/Back To The Light [UK]/Brian May/Back To The Light [UK]

Should be: /home/dan/Music/Brian May/Back To The Light [UK]

So I need to find some way of moving all the files up by two levels...

Thanks in advance! :D

---

### Post by Solver on 2006-12-30
I am no Bash scripter, but this should work.

```

#!/bin/bash
for file in `dir -d *` ; do
mv "$file" ../..
done

```

Put this script into the folder from where you want to move the files. Upon executing, all files (including the script itself) should be moved two levels up, recursively.

---

### Post by viciouslime on 2006-12-30
Thanks, but this just gave:
```
mv: cannot move `ABBA' to `../../ABBA': Permission denied
mv: cannot stat `Lighthouse\\': No such file or directory
mv: cannot stat `Family': No such file or directory
mv: cannot move `AC-DC' to `../../AC-DC': Permission denied
mv: cannot stat `Ludovico\\': No such file or directory
mv: cannot stat `Einaudi': No such file or directory
mv: cannot stat `Alanis\\': No such file or directory
mv: cannot stat `Morissette': No such file or directory
mv: cannot move `Madonna' to `../../Madonna': Permission denied
mv: cannot stat `Alan\\': No such file or directory
mv: cannot stat `Jackson': No such file or directory
mv: cannot stat `Mariah\\': No such file or directory
mv: cannot stat `Carey': No such file or directory
mv: cannot stat `Alex\\': No such file or directory
mv: cannot stat `Parks': No such file or directory
mv: cannot stat `Maroon\\': No such file or directory
... continues as above but for other directories

```

Thanks very much for trying though! :D

---

### Post by viciouslime on 2006-12-30
Ok, I have managed to get a list of every file with the path to it and have managed to use find and replace in gedit to create something like this:
```
mv "/home/dan/Music (oggish)/AC-DC/If You Want Blood You've Got It/AC-DC/If You Want Blood You've Got It/Ac-dc - Bad Boy Boogie.ogg" ../../
mv "/home/dan/Music (oggish)/AC-DC/If You Want Blood You've Got It/AC-DC/If You Want Blood You've Got It/Ac-dc - Hell Ain't A Bad Place To Be.ogg" ../../
mv "/home/dan/Music (oggish)/AC-DC/If You Want Blood You've Got It/AC-DC/If You Want Blood You've Got It/Ac-dc - High Voltage.ogg" ../../
mv "/home/dan/Music (oggish)/AC-DC/If You Want Blood You've Got It/AC-DC/If You Want Blood You've Got It/Ac-dc - Problem Child.ogg" ../../
mv "/home/dan/Music (oggish)/AC-DC/If You Want Blood You've Got It/AC-DC/If You Want Blood You've Got It/Ac-dc - Riff Raff.ogg" ../../
```

Not very elegant, but hey. Now, the only problem is, it is trying to move the file up two places from where I am at the prompt, not up two places from where the file is...](*,)

---

### Post by HadroLepton on 2006-12-31
heh this is a **one-liner** 8)
(just trying to brag, took me some time to assemble this one line)

assuming that all your music files are located under the music folder
type this from your home directory

```
$ find music -type f
```

**find** will search, starting from the directory **music**, all objects of type **file (-type f)**

make sure that the files found are those files, and **only** those files, which you want to be moved
we are going to expand this command so it does the work for us

```
$ find music -type f -printf 'mv "%h/%f" "%h/../.."\n'
```

the **-printf 'foo'** tells find to print **foo** instead of the usual filename
**%h** is the path part of the file
**%f** is the filename part of the file
**mv "%h/%f" "%h/../.."** will become **mv "path/file.mp3" "path/../.."**
the " are there to catch the spaces in the filename
(check man find for more)

now we redirect the output to another file

```
$ find music -type f -fprintf moveuptwodir.sh 'mv "%h/%f" "%h/../.."\n'
```

**-fprintf** works like **-printf** only this time the output goes to the file **moveuptwodir.sh**
check the contents of this file. if all is well then you can execute that file

---

### Post by viciouslime on 2006-12-31
THANK YOU SO MUCH! :D 

Worked PERFECTLY! :mrgreen: :mrgreen: :mrgreen:

---

### Post by madmadchen on 2008-06-20
So, two questions, if anyone's still watching-

_The Practical Question (highest priority):_

I am looking to write a similar script, except instead of moving it two folders up I'm looking to move them to the folder the script is applied to- for example, with structure Desktop-->myFolder-->subFolder-->subSubFolder, if on the command line I enter [font="Courier New"]./script myFolder[/font], anything in subFolder and subSubFolder (and any other directories below myFolder) would be moved to myFolder. 

The only modification I made is line 3: ```
3: mv "$file" $1
```
The slightly modified very short script above by Solver ALMOST works- except it for two issues:

 1) It takes everything in the same folder as myFolder and also and moves them to myFolder- so if I run FMove from Desktop, everything there also ends up in myFolder. Why is this, and how can I fix it?

2) It doesn't move files from subfolders, it just moves the topmost subfolder to myFolder- i.e. subFolder to myFolder, leaving the contents of subFolder as-is. I'm experimenting with recursion at the moment, but that requires checking for folders, which is a pain. If anyone has any better ideas or a working recursive script please let me know.

_The Theory Question (lowest priority):_

I looked up man page for [font="Courier New"]dir [/font]to check out the [font="Courier New"]-d[/font] option, but I'm still wondering why that makes the difference. What is the difference between directory entries (using [FONT="Courier New"]-d[/FONT]) and contents? If I use [font="Courier New"]dir -d [/font]in the command line on the directory topLevel, it prints [font="Courier New"]topLevel[/font], where without the -d it of course prints the files and folder in topLevel. If anyone could explain that to me, I'd be grateful.

Thanks in advance!

---

