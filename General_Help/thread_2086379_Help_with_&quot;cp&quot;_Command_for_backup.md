---
title: "Help with &quot;cp&quot; Command for backup"
date: 2012-11-20
forum: General Help
---

### Post by FepzHz on 2012-11-20
hello,

    I was trying to learn my way around the terminal and there's been one command i haven't been able to understand fully. I started by doing simple commands such as creating a new folder/directory = mkdir 
then i opened nano within the terminal
typed up a txt file and "wrote it" in my home folder (~)
then i tried making a backup copy
I entered 
cp (file name) (new file name and i also tried copying it to another directory)
so it worked and i was able to copy the original file and i just added the word backup to it and i also was able write a copy in my "Backup" folder in my ~ directory
But then i tried to do it with a .odt file and it doesn't work. Is this command limited to .txt files? Also are there any other commands for making backups? 
I plan to use the "Backup" directory i created to copy all my important files and dumping them to a usb, for now, but i will eventually get an external drive to store all my backups. But i plan to use the "Backup" folder as a temporary folder where i will periodically cut and paste all the backups of my files to an external storage device. Is this a good method of backing up if not what would you recommend.

---

### Post by MG&amp;TL on 2012-11-20
What exactly didn't work?You should be able to see an error message.

Nope, *cp* should copy pretty much anything.

That's certainly one way to do it, but there's much better commands for the job. *rsync, duplicity, *and *dd *(careful with this one) are all better ways of doing it, but to be honest you'd be better off with Ubuntu's default backup application, Deja Dup (a *duplicity* frontend), which will automatically backup stuff to a location.

---

### Post by coldcritter64 on 2012-11-20
cp should work with any file type afaik. Could you post the full attempt you made with the .odt file, the command and any output, please? This will let us know if you are entering the correct syntax, or if the problem with the odt file is a permissions problem etc.

For more automated backups (as compared to the "manual' method you note) you could look into packages like rsysnc.

---

### Post by Ender Shadow on 2012-11-20
I would recommend that you gather all of the files that you will want to backup in one folder (with sub-folders to help organize them), and then, whenever you want to backup those files, you can just copy and paste the entire folder (or one or more of the sub-folders)  to wherever you want it.
As for doing  something like that in the terminal, you probably know more than I do about it.

---

### Post by Impavidus on 2012-11-20
cp is not such a nice tool for making backups, even if just because it's so easy to type the wrong command and for example overwrite one backup with the backup of another file. (tar is even worse. I once typed "tar -xvzf" instead of "tar -cvzf", unpacking the archive and restoring the backup instead of making a new one. I changed my backup habits immediately. C and x are adjacent on most keyboards). However, you can use cp (and tar) in a script to make backups. It's a good exercise for people learning bash scripting, and custom backup scripts may be quite handy.

---

### Post by redmk2 on 2012-11-20
You can use *cp* interactively with this ```
cp -i file1 file2
```
If file2 exists the user will be asked whether to overwrite or not.```
cp -i file1 file2
cp: overwrite `file2'?
```

The only way to learn is to play with the commands.  Keep going and ask away!

[COLOR="Blue"]Edit:  This works with the command *rm -i* also.  You will be asked if you really want to remove the file.  the *-i *stands for *interactive.*[/COLOR]

---

### Post by FepzHz on 2012-11-21
I'm sorry, i think when i used "cp" to make a a copy of the file, i made  a mistake in typing the file's name . So, i was able to make a copy of  the file(.odt) within the current directoy it was in. But when i tried  to copy the file to another directory ( the "Backup" dir i created) it  didn't showup when I entered the "ls"command to see if it was copied. Is  it possible to copy the file directly to another folder, or do i have  enter the "mv" command after i make a copy of the file in the directory  where the original file is in? I also tried the deja dup app to backup  the files in my "~". But i would rahter like to learn and use the a  command or commands where I can sync the backup files i have in my  "Backup" folder and sync that directory to Ubunto One; from within the  terminal if its possible. Also, can anyone provide a link to explain the   rsync, duplicity, and dd commands*? *

---

### Post by MG&amp;TL on 2012-11-21
See if following this helps: [http://linuxcommand.org/](http://linuxcommand.org/)

*rsync* is a (very good) copying program, in some ways extending *cp.* See the command *man rsync*.

*duplicity* is a CLI backup program. Again, see [I]man duplicity.

dd [/I]simply dumps the data from one file or device to another file or device. It's very good at doing that, and it's very fast, but it's not particularly sophisticated and is *very* destructive should you, for instance, accidentally dump something onto your main drive, as it would most likely wipe it entirely. I mostly included it for education purposes.

---

### Post by Impavidus on 2012-11-22
> **FepzHz said:**
> Is  it possible to copy the file directly to another folder, or do i have  enter the "mv" command after i make a copy of the file in the directory  where the original file is in?
Yes, *cp* will copy files to whatever directory you want, provided the directory already exists. It can also copy a bunch of files to one directory, operate recursively to copy the contents of a directory to another directory...
Type```
man cp
``` and read the manual page (manual pages are available for (almost) every command).

---

