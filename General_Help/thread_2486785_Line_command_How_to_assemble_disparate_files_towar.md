---
title: "Line command How to assemble disparate files toward one folder ?"
date: 2023-05-10
forum: General Help
---

### Post by HuTkW$* on 2023-05-10
Hello !

I desperately looking for reunite files disseminated in many folders, sub folders and several hard disk according to one criteria, then copy to a single folder.

For instance, i would like to assemble all ods files : *.ods -or .pdf-, disseminated in many folders, sub folders and hard disk, then copy to one single folder, by line command.
However, not specific to ubuntu.

Any suggestion ?


Thanks !

---

### Post by yancek on 2023-05-10
There are quite a few sites describing the find command to find specific type files (pdf) and then mv or cp them all to a specific directory.  The complication you have is multiple directories and multiple drives.  One of the examples is listed below which will recursively cp pdf files from a folder and sub-folders to a specific destination directory.

> cp -rf  /sourcepath/sourcedir/*.pdf /destpath/destdir/  

The command below creates a text file named pdf with a list of all pdf files on the system in your /home/username directory which could be useful to determine later if all files were copied/moved.  I would suggest copying before moving.

```
 find / -name "*.pdf" > /home/username/pdf
```

Some other examples at the links below.

 [https://askubuntu.com/questions/696379/how-to-copy-only-pdf-from-folders-and-subfolders](https://askubuntu.com/questions/696379/how-to-copy-only-pdf-from-folders-and-subfolders)
[https://www.2daygeek.com/copy-files-folders-linux-cp-command/](https://www.2daygeek.com/copy-files-folders-linux-cp-command/)

I'm not a programmer so can't help any more but you might need to write a script to cp/mv your files from various destinations to the single destination you want.

---

### Post by MAFoElffen on 2023-05-11
You just said "Copy"
```

sudo find / \( -name '*.obs' -o -name '*.pdf' \) 2> /dev/null | grep -v '^/usr/\|snap\|flatpak' | xargs -I{} cp -u {} /destination/path/

```

---

### Post by TheFu on 2023-05-11
> **exystenz said:**
>  
For instance, i would like to assemble all ods files : *.ods -or .pdf-, disseminated in many folders, sub folders and hard disk, then copy to one single folder, by line command.

Sometimes running 2 commands is easier. ... do you want a copy or a move?

```
$ find ~/ -iname \*ods -exec cp "{}"  /location/you/want/everything \;
$ find ~/ -iname \*pdf -exec cp "{}"  /location/you/want/everything \;

```

For find, which can be very complex, I like to use [https://explainshell.com/](https://explainshell.com/) to get the command correct.  Try it with the commands above.  I prefer using \*ods rather than "*ods" ... personal preference.

[LIST]
[*]~/ is where to look for files. ~/ is the current user's HOME directory.  Can be anywhere - absolute or relative path.
[*]-iname is case-insensitive.
[*]-exec says to run a command.  If you have 500+ files found, you would want to optimize the **cp** with **parallel** or **xargs**, probably.
[*]{} says to insert the found filename, 1 at a time. Because these names could have odd characters or spaces, best to quote that.
[*]/location/you/want/everything ... can be a full/absolute path or relative path from the CWD/PWD.
[*]the trailing \; says the -exec command is done.
[*]
[/LIST]
ExplainShell will show a manpage with the options in the command. Very helpful.

There are 500 possible solutions to this.  **Find** is the easiest that already exists.

---

### Post by HuTkW$* on 2023-06-25
Thanks to all of you !

---

